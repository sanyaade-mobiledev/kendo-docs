---
title: kendo.ui.Grid
meta_title: Grid widget configuration guide, methods and events
meta_description: Code examples for Grid UI widget configuration, learn how to use methods and which events to set once the grid UI widget detail is initialized and expanded.
slug: web-kendo.ui.grid
tags: api,web
publish: true
---

# kendo.ui.Grid

Represents the Kendo UI Grid widget. Inherits from [Widget](/api/framework/widget).

## Configuration

### altRowTemplate `Function`

Template to be used for rendering the alternate rows in the grid.

#### Example

    //template
    <script id="altRowTemplate" type="text/x-kendo-tmpl">
        <tr class="k-alt">
            <td>
                <img src="${ BoxArt.SmallUrl }" alt="${ Name }" />
            </td>
            <td>
                ${ Name }
            </td>
            <td>
                ${ AverageRating }
            </td>
        </tr>
    </script>

    //grid intialization
    <script>PO details informaiton
        $("#grid").kendoGrid({
            dataSource: dataSource,
            altRowTemplate: kendo.template($("#altRowTemplate").html()),
            height: 200
        });
    </script>

### autoBind `Boolean`*(default: true)*

 Indicates whether the grid will call read on the DataSource initially.

#### Example

    $("#grid").kendoGrid({
         dataSource: sharedDataSource,
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 template: '#= kendo.toString(BirthDate,"dd MMMM yyyy") #'
            }
         ],
         autoBind: false // the grid will not be populated with data until read() is called on the sharedDataSource
     });

### columns `Array`

A collection of column objects or collection of strings that represents the name of the fields.

#### Example

    var sharedDataSource = new kendo.data.DataSource({
         data: [{title: "Star Wars: A New Hope", year: 1977}, {title: "Star Wars: The Empire Strikes Back", year: 1980}],
         pageSize: 1
    });
    $("#grid").kendoGrid({
        dataSource: sharedDataSource,
        columns: [ { title: "Action", command: "destroy" }, // creates a column with delete buttons
                   { title: "Title", field: "title", width: 200, template: "<div id='title'>${ title }</div>" },
                   { title: "Year", field: "year", filterable: false, sortable: true, format: "{0:dd/MMMM/yyyy}" } ]
    });

### columns.attributes `Object`

Definition of column cells' HTML attributes. Reserved words in Javascript should be enclosed in quotation marks.

#### Example

    $("#grid").kendoGrid({
        columns: [
            {
                field: "Price",
                attributes: {
                    "class": "myClass",
                    style: "text-align: right"
                }
            }
        ]
    });

### columns.command `String|Array`

Definition of command column. The supported built-in commands are: "create", "cancel", "save", "destroy".

### columns.command.name `String`

The unique name of the command. The supported built-in commands are: "create", "cancel", "save", "destroy".

### columns.command.text `String`

The text displayed by the command.

### columns.command.className `String`

The CSS class of the command.

### columns.command.click `Function`

The JavaScript function executed when the user clicks the command button.

### columns.editor `Function`

Provides a way to specify custom editor for this column.

#### Example

    $(".k-grid").kendoGrid({
         dataSource: {
             data: createRandomData(50)
         },
         editable: true,
         columns: [
             {
                 field: "Name",
                 editor: function(container, options) {
                     // create a KendoUI AutoComplete widget as column editor
                      $('<input name="' + options.field + '"/>')
                          .appendTo(container)
                          .kendoAutoComplete({
                              dataTextField: "ProductName",
                              dataSource: {
                                  transport: {
                                    //...
                                  }
                              }
                          });
                 }
             }
         ]
      });

### columns.encoded `Boolean`*(default: true)*

 Specified whether the column content is escaped. Disable encoding if the data contains HTML markup.

### columns.field `String`

The field from the datasource that will be displayed in the column.

### columns.filterable `Boolean | Object`*(default: true)*

Specifies whether given column is filterable.

### columns.filterable.ui `String | Function`

Role of the widget shown as column filter menu input element.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Event",
                 filterable: {
                    ui: "datetimepicker"
                 }
            }
         ]
      });

Function which to be called in order to create the widget for the column filter menu input elements.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Event",
                 filterable: {
                    ui: function(element) {
                        element.kendoDateTimePicker();
                    }
                 }
            }
         ]
      });

### columns.format `String`

The format that will be applied on the column cells.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 format: "{0:dd/MMMM/yyyy}"
            }
         ]
      });

### columns.headerAttributes `Object`

Definition of column header cell's HTML attributes. Reserved words in Javascript should be enclosed in quotation marks.

#### Example

    $("#grid").kendoGrid({
        columns: [
            {
                field: "Price",
                headerAttributes: {
                    "class": "myHeader",
                    style: "text-align: right"
                }
            }
        ]
    });

### columns.headerTemplate `String`

The template for column's header cell. If sorting is enabled, it will be wrapped in a `<a class="k-link">` element, so the template should consist of only inline elements
in order to have valid HTML markup in the Grid.

#### Example

    $("#grid").kendoGrid({
         columns: [
             {
                 headerTemplate: '<input type="checkbox" id="checkAll" />'
            }
         ]
      });

### columns.hidden `Boolean`*(default: false)*

Specifies whether given column is hidden.

### columns.sortable `Boolean`*(default: true)*

 Specifies whether given column is sortable.

### columns.template `String`

The template for column's cells.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 template: '#= kendo.toString(BirthDate,"dd MMMM yyyy") #'
            }
         ]
      });

### columns.aggregates `Array`

The aggregates to be used when grouping is applied

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "UnitPrice",
                 aggregates: ["count", "sum"]
             }
         ]
      });


### columns.groupHeaderTemplate `String`

The template for group header item.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10,
             group: { field: "BirthDate" }
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 groupHeaderTemplate: 'Birth Date: #= value #'
            }
         ]
      });

### columns.groupFooterTemplate `String`

The template for column's cell in group footer item.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10,
             group: { field: "BirthDate" }
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 groupFooterTemplate: 'custom text'
            }
         ]
      });

### columns.footerTemplate `String`

The template for column's cell in footer item.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 footerTemplate: 'custom footer text'
            }
         ]
      });

### columns.title `String`

The text that will be displayed in the column header.

### columns.width `String`

The width of the column.

### columns.menu `Boolean`

Indicates whether the column should be visible in column menu.

### columnMenu `Boolean | Object`

Enables column header menu

### columnMenu.columns `Boolean`

Enable/disable columns section in column header menu.

### columnMenu.filterable `Boolean`

Enable/disable filter section in column header menu.

### columnMenu.sortable `Boolean`

Enable/disable sorting section in column header menu.

### columnMenu.messages `Object`

Sets the columnMenu messages.

#### Example

    columnMenu: {
        messages: {
            sortAscending: "Sort Ascending",
            sortDescending: "Sort Descending",
            filter: "Filter",
            columns: "Columns"
        }
    }

### columnMenu.messages.columns `String`

Set the text of the columns section in column header menu.

### columnMenu.messages.filter `String`

Set the text of the filter section in column header menu.

### columnMenu.messages.sortAscending `String`

Set the text of the sortAscending section in column header menu.

### columnMenu.messages.sortDescending `String`

Set the text of the sortDescending section in column header menu.

### dataSource `kendo.data.DataSource | Object`

Instance of DataSource or Object with DataSource configuration.

#### Example

    var sharedDataSource = new kendo.data.DataSource({
         data: [{title: "Star Wars: A New Hope", year: 1977}, {title: "Star Wars: The Empire Strikes Back", year: 1980}],
         pageSize: 1
    });

    $("#grid").kendoGrid({
         dataSource: sharedDataSource
     });

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: [{title: "Star Wars: A New Hope", year: 1977}, {title: "Star Wars: The Empire Strikes Back", year: 1980}],
             pageSize: 1
         }
     });

### detailTemplate `Function`

Template to be used for rendering the detail rows in the grid.
See the [**Detail Template**](http://demos.kendoui.com/web/grid/detailtemplate.html) example.

### editable `Boolean|Object` *(default: false)*

Indicates whether editing is enabled/disabled.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 template: '#= kendo.toString(BirthDate,"dd MMMM yyyy") #'
            }
         ]
         toolbar: [
             "create",
             { name: "save", text: "Save This Record" },
             { name: "cancel", template: "<img src="icons/cancel.png' rel='cancel' />" }
         ],
         editable: {
             update: true, // puts the row in edit mode when it is clicked
             destroy: false, // does not remove the row when it is deleted, but marks it for deletion
             confirmation: "Are you sure you want to remove this item?"
         }
     });

### editable.confirmation `Boolean | String`

Defines the text that will be used in confirmation box when delete an item.

### editable.createAt `String`

Indicates whether the created record should be inserted at the top or at the bottom of the current page. Available values are "top" and "bottom".

### editable.destroy `Boolean`

Indicates whether item should be deleted when click on delete button.

### editable.mode `String`

Indicates which of the available edit modes(incell(default)/inline/popup) will be used

### editable.template `String`

Template which will be use during popup editing

### editable.update `Boolean`

Indicates whether item should be switched to edit mode on click.

### filterable `Boolean | Object`*(default: false)*

 Indicates whether filtering is enabled/disabled.

### filterable.extra `Boolean`*(default: true)*

 Indicates whether second filter input is enabled/disabled.

### filterable.messages `Object`

 Sets the filter menu messages.

#### Example

    filterable: {
        messages: {
            info: "Custom header text:", // sets the text on top of the filter menu
            filter: "CustomFilter", // sets the text for the "Filter" button
            clear: "CustomClear", // sets the text for the "Clear" button
            
            // when filtering boolean numbers
            isTrue: "custom is true", // sets the text for "isTrue" radio button
            isFalse: "custom is false", // sets the text for "isFalse" radio button
            
            //changes the text of the "And" and "Or" of the filter menu
            and: "CustomAnd",
            or: "CustomOr"
        }
    }

### filterable.messages.and `String`

 Set the text of the "and" option from logic drop down list.

### filterable.messages.clear `String`

 Set the text of the clear button of the filter menu.

### filterable.messages.filter `String`

 Set the text of the filter button of the filter menu.

### filterable.messages.info `String`

 Set the text of the information message on top of the filter menu.

### filterable.messages.isFalse `String`

 Set the text of the isFalse radio button of the filter menu for boolean values.

### filterable.messages.isTrue `String`

 Set the text of the isTrue radio button of the filter menu for boolean values.

### filterable.messages.or `String`

 Set the text of the "or" option from logic drop down list.

### filterable.messages.selectValue `String`

 Set the text of the option label for foreign key drop down list.

### filterable.operators `Object`

 Enable/Disable and set the text of filter operators.

### filterable.operators.string `Object`

 Enable/Disable and set the text of filter operators for fields of type string.

> **Important:** Omitting an operator will exclude it from the list of available operators in the filter menu.

### filterable.operators.string.eq `String`

 Enable/Disable and set the text of the "Is equal to" filter option for columns with string values.

### filterable.operators.string.neq `String`

 Enable/Disable and set the text of the "Is not equal to" filter option for columns with string values.

### filterable.operators.string.startswith `String`

 Enable/Disable and set the text of the "Starts with" filter option for columns with string values.

### filterable.operators.string.contains `String`

 Enable/Disable and set the text of the "Contains" filter option for columns with string values.

### filterable.operators.string.doesnotcontain `String`

 Enable/Disable and set the text of the "Does not contain" filter option for columns with string values.

### filterable.operators.string.endswith `String`

 Enable/Disable and set the text of the "Ends with" filter option for columns with string values.

### filterable.operators.number `Object`

 Enable/Disable and set the text of filter operators for fields of type number.

> **Important:** Omitting an operator will exclude it from the list of available operators in the filter menu.

### filterable.operators.number.eq `String`

 Enable/Disable and set the text of the "Is equal to" filter option for columns with number values.

### filterable.operators.number.neq `String`

 Enable/Disable and set the text of the "Is not equal to" filter option for columns with number values.

### filterable.operators.number.gte `String`

 Enable/Disable and set the text of the "Is greater than or equal to" filter option for columns with number values.

### filterable.operators.number.gt `String`

 Enable/Disable and set the text of the "Is greater than" filter option for columns with number values.

### filterable.operators.number.lte `String`

 Enable/Disable and set the text of the "Is less than or equal to" filter option for columns with number values.

### filterable.operators.number.lt `String`

 Enable/Disable and set the text of the "Is less than" filter option for columns with number values.

### filterable.operators.date `Object`

 Enable/Disable and set the text of filter operators for fields of type date.

> **Important:** Omitting an operator will exclude it from the list of available operators in the filter menu.

### filterable.operators.date.eq `String`

 Enable/Disable and set the text of the "Is equal to" filter option for columns with date values.

### filterable.operators.date.neq `String`

 Enable/Disable and set the text of the "Is not equal to" filter option for columns with date values.

### filterable.operators.date.gte `String`

 Enable/Disable and set the text of the "Is after or equal to" filter option for columns with date values.

### filterable.operators.date.gt `String`

 Enable/Disable and set the text of the "Is after" filter option for columns with date values.

### filterable.operators.date.lte `String`

 Enable/Disable and set the text of the "Is before or equal to" filter option for columns with date values.

### filterable.operators.date.lt `String`

 Enable/Disable and set the text of the "Is before" filter option for columns with date values.

### filterable.operators.enums `Object`

 Enable/Disable and set the text of filter operators for foreign key columns.

> **Important:** Omitting an operator will exclude it from the list of available operators in the filter menu.

### filterable.operators.enums.eq `String`

 Enable/Disable and set the text of the "Is equal to" filter option for foreign key columns.

### filterable.operators.enums.neq `String`

 Enable/Disable and set the text of the "Is not equal to" filter option for foreign key columns.

### reorderable `Boolean`*(default:false)*

 Indicates whether column reordering is enabled/disable.

### resizable `Boolean`*(default:false)*

 Indicates whether column resizing is enabled/disable.

### groupable `Boolean | Object`*(default: false)*

 Indicates whether grouping is enabled/disabled.

#### Example

    $("#grid").kendoGrid({
         filterable: true
    });

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 template: '#= kendo.toString(BirthDate,"dd MMMM yyyy") #'
            }
         ],
         groupable: true
    });

### groupable.messages `Object`

 Sets the messages displayed during grouping.

### groupable.messages.empty `String`

 Sets the text of the empty grouping area message

#### Example

    $("#grid").kendoGrid({
        groupable: {
            messages: {
                empty: "Custom message text"
            }
        }
    });

### height `Number|String`

 Sets the height of the grid.

### navigatable `Boolean`*(default: false)*

 Indicates whether keyboard navigation is enabled/disabled.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 template: '#= kendo.toString(BirthDate,"dd MMMM yyyy") #'
            }
         ],
         navigatable: true
     });

### pageable `Boolean | Object`*(default: false)*

 Indicates whether paging is enabled/disabled.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 template: '#= kendo.toString(BirthDate,"dd MMMM yyyy") #'
            }
         ],
         pageable: true
     });

### pageable.pageSize `Number`

  Defines the number of records which will be displyed.

### pageable.previousNext `Boolean`*(default: true)*

  Defines if buttons for navigating to the first, last, previous and next pages will be shown.

### pageable.numeric `Boolean`*(default: true)*

  Defines if numeric portion of the pager will be shown.

### pageable.buttonCount `Number`*(default: 10)*

  Defines the number of buttons displayed in the numeric pager.

### pageable.input `Boolean`*(default: false)*

  Defines if an input element which allows the user to navigate to given page will be displayed.

### pageable.pageSizes `Boolean | Array`*(default: false | [5,10,20])*

  Displayes a list with predefined page sizes. An array of values to be displayed can be provided.

### pageable.refresh `Boolean`*(default: false)*

  Defines if a refresh button will be displayed.

### pageable.info `Boolean`*(default: true)*

  Defines if a label showing current paging information will be displayed.

### pageable.messages `Object`

  Defines texts shown within the pager.

### pageable.messages.display `String`*(default: "{0} - {1} of {2} items")*,

  Defines the info text.

### pageable.messages.empty `String`*(default: "No items to display")*,

  Defines the info text shown when there are no records to be displayed.

### pageable.messages.page `String`*(default: "Page")*,

  Defines the first part of the text of the input option.

### pageable.messages.of `String`*(default: "of {0}")*,

  Defines the last part of the text of the input option.

### pageable.messages.itemsPerPage `String`*(default: "items per page")*,

  Defines the text displayed after the select element of the pageSizes mode.

### pageable.messages.first `String`*(default: "Go to the first page")*,

  Defines the text of the first page button tooltip.

### pageable.messages.previous `String`*(default: "Go to the previous page")*,

  Defines the text of the previous page button tooltip.

### pageable.messages.next `String`*(default: "Go to the next page")*,

  Defines the text of the next page button tooltip.

### pageable.messages.last `String`*(default: "Go to the last page")*,

  Defines the text of the last page button tooltip.

### pageable.messages.refresh `String`*(default: "Refresh")*,

  Defines the text of the refresh button tooltip.

### rowTemplate `Function`

Template to be used for rendering the rows in the grid.

#### Example

    //template
     <script id="rowTemplate" type="text/x-kendo-tmpl">
         <tr>
             <td>
                 <img src="${ BoxArt.SmallUrl }" alt="${ Name }" />
             </td>
             <td>
                 ${ Name }
             </td>
             <td>
                 ${ AverageRating }
             </td>
         </tr>
     </script>

     //grid intialization
     <script>PO details informaiton
         $("#grid").kendoGrid({
             dataSource: dataSource,
             rowTemplate: kendo.template($("#rowTemplate").html()),
             height: 200
         });
     </script>

### scrollable `Boolean | Object`*(default: true)*

 Enable/disable grid scrolling.

### scrollable.virtual `Boolean` *(default: false)*

 Enable/disable virtual scrolling. When enabled the grid will display only a single page of data (configured via `dataSource.pageSize`).

#### Example

    $("#grid").kendoGrid({
         scrollable: {
             virtual: true //false
         }
     });

### selectable `String`*(default: undefined)*

 Indicates whether selection is enabled/disabled. Possible values:


#### *"row"*

Single row selection.

#### *"cell"*

Single cell selection.

#### *"multiple, row"*

Multiple row selection.

#### *"multiple, cell"*

Multiple cell selection.

### sortable `Boolean|Object`

Defines whether grid columns are sortable.

#### Example

    $("#grid").kendoGrid({
        sortable: true
    });
    //
    // or
    //
    $("#grid").kendoGrid({
        sortable: {
            mode: "multiple", // enables multi-column sorting
            allowUnsort: true
    });

### sortable.allowUnsort `Boolean`*(default: false)*

  Defines whether column can have unsorted state.

### sortable.mode `String`*(default: "single")*

 Defines sorting mode. Possible values:


#### *"single"*

Defines that only once column can be sorted at a time.

#### *"multiple"*

Defines that multiple columns can be sorted at a time.

### toolbar `Array`

This is a list of commands for which the corresponding buttons will be rendered.
The supported built-in commands are: "create", "cancel", "save", "destroy".
Or template to be used for rendering the toolbar content.

#### Example

    $("#grid").kendoGrid({
         dataSource: {
             data: createRandomData(50),
             pageSize: 10
         },
         columns: [
             {
                 field: "Name"
             },
             {
                 field: "BirthDate",
                 title: "Birth Date",
                 template: '#= kendo.toString(BirthDate,"dd MMMM yyyy") #'
            }
         ]
         toolbar: [
             "create",
             { name: "save", text: "Save This Record" },
             { name: "cancel", template: '<img src="icons/cancel.png' rel='cancel' />" }
         ],
         editable: true
      });

### toolbar.name `String`

The name of the command. One of the predefined or a custom.

### toolbar.template `String`

The template for the command button.

### toolbar.text `String`

The text of the command that will be set on the button.

## Methods

### addRow

Adds a new empty table row in edit mode. The addRow method triggers edit event.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    grid.addRow();

### cancelChanges

Cancels any pending changes during. Deleted rows are restored. Inserted rows are removed. Updated rows are restored to their original values.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    grid.cancelChanges();

### cancelRow

Switch the current edited row into display mode and revert changes made to the data

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    grid.cancelRow();

### cellIndex

Returns the index of the cell in the grid item skipping group and hierarchy cells.

#### Example

     // get a reference to the grid widget
     var grid = $("#grid").data("kendoGrid");
     // get the index of the currently edited cell
     grid.cellIndex(grid.tbody.find(">tr td.k-edit-cell"));

#### Parameters

##### cell `Selector | DOM Element`

Target cell.

### clearSelection

Clears currently selected items.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // clear the selection of items in the grid
    grid.clearSelection();

### closeCell

Closes current edited cell.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // close the cell being edited
    grid.closeCell();

### collapseGroup

Collapses specified group.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // collapses first group item
    grid.collapseGroup(grid.tbody.find(">tr.k-grouping-row:first"));

#### Parameters

##### group `Selector | DOM Element`

Target group item to collapse.

### collapseRow

Collapses specified master row.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // collapses first master row
    grid.collapseRow(grid.tbody.find(">tr.k-master-row:first"));

#### Parameters

##### row `Selector | DOM Element`

Target master row to collapse.

### dataItem

Returns the data item to which a given table row (tr DOM element) is bound.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // returns the data item for first row
    grid.dataItem(grid.tbody.find(">tr:first"));

#### Parameters

##### tr `Selector | DOM Element`

Target row.

### destroy
Prepares the **Grid** for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> **Important:** This method does not remove the Grid element from DOM.

#### Example

    var grid = $("#grid").data("kendoGrid");

    // detach events
    grid.destroy();

### editCell

Puts the specified table cell in edit mode. It requires a jQuery object representing the cell. The editCell method triggers edit event.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // edit first table cell
    grid.editCell(grid.tbody.find(">tr>td:first"));

#### Parameters

##### cell `Selector`

Cell to be edited.

### editRow

Switches the specified row from the grid into edit mode. The editRow method triggers edit event.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // edit first table row
    grid.editRow(grid.tbody.find(">tr:first"));

#### Parameters

##### row `Selector | DOM Element`

Row to be edited.

### expandGroup

Expands specified group.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // expands first group item
    grid.expandGroup(grid.tbody.find(">tr.k-grouping-row:first"));

#### Parameters

##### group `Selector | DOM Element`

Target group item to expand.

### expandRow

Expands specified master row.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // expands first master row
    grid.expandRow(grid.tbody.find(">tr.k-master-row:first"));

#### Parameters

##### row `Selector | DOM Element`

Target master row to expand.

### hideColumn

Hides the specified column.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");

    // hide the "id" column
    grid.hideColumn("id");

    // hide the 3rd column
    grid.hideColumn(2);

#### Parameters

##### column `Number | String`

The index or the bound field of the column to hide.

### refresh

Redraws the grid using the current data of the DataSource.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // refreshes the grid
    grid.refresh();


### removeRow

Removes the specified row from the grid. The removeRow method triggers remove event.
(Note: In inline or popup edit modes the changes will be automatically synced)

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // remove first table row
    grid.removeRow(grid.tbody.find(">tr:first"));

#### Parameters

##### row `Selector | DOM Element`

Row to be removed.

### reorderColumn

Changes the position of the specified column.

#### Example
    //get reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    //move first column (index is zero based)
    grid.reorderColumn(2, grid.columns[0]);

#### Parameters

##### destIndex `number`

##### column `grid column`

### saveChanges

Calls DataSource sync to submit any pending changes if state is valid. The saveChanges method triggers saveChanges event.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    grid.saveChanges();

### saveRow

Switch the current edited row into dislay mode and save changes made to the data
(Note: the changes will be automatically synced)

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    grid.saveRow();

### select

Selects the specified Grid rows/cells. If called without arguments - returns the selected rows/cells.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");
    // selects first grid item
    grid.select(grid.tbody.find(">tr:first"));

#### Parameters

##### items `Selector | Array`

Items to select.

### setDataSource

Sets the dataSource of an existing Grid and rebinds it.

### Example

    var dataSource = new kendo.data.DataSource({
        //dataSource configuration
    });

    $("#grid").data("kendoGrid").setDataSource(dataSource);

### showColumn

Shows the specified column.

#### Example

    // get a reference to the grid widget
    var grid = $("#grid").data("kendoGrid");

    // show the "id" column
    grid.showColumn("id");

    // show the 3rd column
    grid.showColumn(2);

#### Parameters

##### column `Number | String`

The index or the bound field of the column to show.

## Events

### change

Fires when the grid selection has changed.

#### Example

     $("#grid").kendoGrid({
         change: function() {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the change event
     grid.bind("change", function() {
         // handle event
     });

#### Example - getting the selected data item(s) when using row selection

     $("#grid").kendoGrid({
         selectable: "multiple",
         change: function() {
            var selectedRows = this.select();

            var selectedDataItems = [];

            for (var i = 0; i < selectedRows.length; i++) {
                var dataItem = this.dataItem(selectedRows[i]);

                selectedDataItems.push(dataItem);
            }

            // selectedDataItems now contains all selected data records
         }
     });

#### Example - getting the selected data item(s) when using cell selection

     $("#grid").kendoGrid({
         selectable: "multiple cell",
         change: function() {
            var selectedCells = this.select();

            var selectedDataItems = [];

            for (var i = 0; i < selectedCells.length; i++) {
                var dataItem = this.dataItem(selectedCells[i].parentNode);

                // Check if the dataItem is not already added. Uses http://api.jquery.com/jQuery.inArray
                if ($.inArray(dataItem, selectedDataItems) < 0) {
                    selectedDataItems.push(dataItem);
                }
            }

            // selectedDataItems now contains all selected data records
         }
     });

### columnHide

Fires when the user hides a column.

#### Example

     $("#grid").kendoGrid({
         columnHide: function(e) {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the columnReorder event
     grid.bind("columnHide", function(e) {
         // handle event
     });

#### Event Data

##### e.column `Object`

The column object with its properties, e.g. `encoded`, `field` and `title`.

### columnReorder

Fires when the user changes the order of a column.

#### Example

     $("#grid").kendoGrid({
         columnReorder: function(e) {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the columnReorder event
     grid.bind("columnReorder", function(e) {
         // handle event
     });

#### Event Data

##### e.column `Object`

The column object with its properties, e.g. `encoded`, `field` and `title`.

##### e.newIndex `Number`

The new column index.

##### e.oldIndex `Number`

The previous column index.

### columnResize

Fires when the user resizes a column.

#### Example

     $("#grid").kendoGrid({
         columnResize: function(e) {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the columnResize event
     grid.bind("columnResize", function(e) {
         // handle event
     });

#### Event Data

##### e.column `Object`

The column object with its properties, e.g. `encoded`, `field` and `title`.

##### e.oldWidth `Number`

The previous column width.

##### e.newWidth `Number`

The new column width.

### columnShow

Fires when a column is shown.

#### Example

     $("#grid").kendoGrid({
         columnShow: function(e) {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the columnReorder event
     grid.bind("columnShow", function(e) {
         // handle event
     });

#### Event Data

##### e.column `Object`

The column object with its properties, e.g. `encoded`, `field` and `title`.

### dataBound

Fires when the grid has received data from the data source.

#### Example

     $("#grid").kendoGrid({
         dataBound: function(e) {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the dataBound event
     grid.bind("dataBound", function(e) {
         // handle event
     });

### dataBinding

Fires when the grid is about to be rendered.

#### Example

     $("#grid").kendoGrid({
         dataBinding: function(e) {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the dataBound event
     grid.bind("dataBinding", function(e) {
         // handle event
     });


### detailCollapse

Fires when the grid detail row is collapsed.

#### Example

     $("#grid").kendoGrid({
         detailCollapse: function(e) {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the detailCollapse event
     grid.bind("detailCollapse", function(e) {
         // handle event
     });

#### Event Data

##### e.masterRow `Object`

The jQuery element representing master row.

##### e.detailRow `Object`

The jQuery element representing detail row.

### detailExpand

Fires when the grid detail row is expanded.

#### Example

     $("#grid").kendoGrid({
         detailExpand: function(e) {
             // handle event
         }
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the detailExpand event
     grid.bind("detailExpand", function(e) {
         // handle event
     });

#### Event Data

##### e.masterRow `Object`

The jQuery element representing master row.

##### e.detailRow `Object`

The jQuery element representing detail row.

### detailInit

Fires when the grid detail is initialized.

#### Example

     $("#grid").kendoGrid({
         detailInit: function(e) {
             // handle event
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the detailInit event
     grid.bind("detailInit", function(e) {
         // handle event
     });

#### Event Data

##### e.masterRow `Object`

The jQuery element representing master row.

##### e.detailRow `Object`

The jQuery element representing detail row.

##### e.detailCell `Object`

The jQuery element representing detail cell.

##### e.data `Object`

The data for the master row.

### edit

Fires when the grid enters edit mode.

#### Example

     $("#grid").kendoGrid({
         edit: function(e) {
             // handle event
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the edit event
     grid.bind("edit", function(e) {
         // handle event
     });

#### Event Data

##### e.container `Object`

The jQuery element to be edited.

##### e.model `Object`

The model to be edited.

### remove

Fires before the grid item is removed.

#### Example

     $("#grid").kendoGrid({
         remove: function(e) {
             // handle event
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the remove event
     grid.bind("remove", function(e) {
         // handle event
     });

#### Event Data

##### e.row `Object`

The row element to be deleted.

##### e.model `Object`

The model which to be deleted.

### save

Fires before the grid item is changed.

#### Example

     $("#grid").kendoGrid({
         save: function(e) {
             // handle event
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the save event
     grid.bind("save", function(e) {
         // handle event
     });

#### Event Data

##### e.values `Object`

The values entered by the user.

##### e.container `Object`

The jQuery element which is in edit mode.

##### e.model `Object`

The edited model.

### saveChanges

Fires before the grid calls DataSource sync.

#### Example

     $("#grid").kendoGrid({
         saveChanges: function(e) {
             // handle event
     });

#### To set after initialization

     // get a reference to the grid
     var grid = $("#grid").data("kendoGrid");
     // bind to the saveChanges event
     grid.bind("saveChanges", function(e) {
         // handle event
     });
