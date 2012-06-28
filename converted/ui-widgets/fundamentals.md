---
title: Fundamentals
publish: true
---

### Widget initialization

Since Kendo UI is built on top of jQuery, using the new UI widgets is very intuitive. For example, to use the new Kendo AutoComplete, first you’d write some standard HTML:

  
    <input id="myAutoComplete" />  

Then, to initialize this HTML input and give it the Kendo functionality and styling, a single jQuery JavaScript line is required:
  
    $("#myAutoComplete").kendoAutoComplete(["Apples", "Oranges", "Grapes"]);  

### Widget configuration

To additionally configure the widgets you should provide JSON-formatted settings to the widget constructor. The specific property names and configuration options for each widget can be found in the online demo documentation. For example:
  
      $("#grid").kendoGrid({
          columns:[
              {
                  field: "FirstName",
                  title: "First Name"
              },
              {
                  field: "LastName",
                  title: "Last Name"
          }],
          dataSource: {
              data: [
                  {
                      FirstName: "Joe",
                      LastName: "Smith"
                  },
                  {
                      FirstName: "Jane",
                      LastName: "Smith"
              }]
          }
      });
      

### 
Getting widget client object

The widget client object is preserved in the [data store](http://docs.jquery.com/core/data "jQuery data store") for the corresponding element.&nbsp;The following code snippet shows how to get the client object of the grid widget.&nbsp;
  
    //the name of the data key is built by adding "kendo" prefix to the widget's name
    var grid = $("#grid").data("kendoGrid");
      

### Widget event binding

There are two ways of subscribing to the widget events:

*   by providing handler in the configuration during widget initialization
*   by using **bind** method  

#### Subscribing during widget initialization
 
     $("#products").kendoAutoComplete({
    dataSource: data,
    change: onChange,
    close: onClose,
    open: onOpen
    });
       

#### Subscribing via bind method
 
    var autoComplete = $("#products").data("kendoAutoComplete");
    autoComplete.bind("change", onChange);
      

The handler is a callback function, as shown bellow. Within the handler, the keyword _"this"_ refers to the Kendo widget to which the handler is subscribed.
  
    <script type="text/javascript">
     function onChange(args) {
      //"this" refers to the AutoComplete widget that triggers the event
     }
    </script>
      

### Declarative widget initialization based on data attributes

In addition to the jQuery plugin initialization, each kendo widget can be
initialized and configured by setting a `role` data attribute
on the target element and calling `kendo.init` on its element or any of its containers.
  

#### Initialize a kendo DropDownList using a role attribute
 
    <div id="container">
    <select data-role="dropdownlist"></select>
    
    
    <script>
    kendo.init($("#container"));
    </script>
     </div> 

The role attribute value is the name of the widget, lower case.

#### Configuration

Each widget configuration option can be specified as a data attribute to the respective element.
Camel-cased options are translated to dash separated attributes. Options, which start
with `data` do not require an additional "data" in the attribute name. For instance,
dataTextField option of the autocomplete widget can be specified with
`data-text-field="foo"` attribute.
  

#### Configure kendo DropDownList with data attributes
 
    <select data-role="dropdownlist" data-delay="1000">
    </select>
      

#### Events / DataSource

A widget event can be bound using data attributes too. The value of the data attribute will be resolved to a
function, available in the global scope.
  

#### Bind to dropDownList change event
 
    <select data-role="dropdownlist" data-change="foo">
    </select>
    <script>
    function foo(e) {
        // ...
    }
    </script>
      

Event handlers also support member functions, using javascript syntax. An event handler can be specified using
`foo.bar`, resolving to the member method `bar` of the object `foo`.
  

#### Bind to dropDownList change event to a member function
 
    <select data-role="dropdownlist" data-change="foo.bar">
    </select>
    <script>
    var foo = {
        bar: function(e) {
            // ...
        }
    }
    </script>
      

The **declarative DataSource** binding works in the same way, expecting a DataSource object or an array.
  

#### Specify DropDownList DataSource
 
    <select data-role="dropdownlist" data-source="foo">
    </select>
    <script>
    var foo = ["foo", "bar", "baz"];
    </script>
      

## Templates

For widgets that have template configuration options, the data attribute value will be resolved to an id of a script
element, with the contents of the template.
  

#### Specify DropDownList Template
 
    <select data-role="dropdownlist" data-template="foo"></select>
    <script id="foo" type="script/x-kendo-template">
    <span>#:data.Name</span>
    </script>
     