---
title: editor-imagebrowser-schema-model-fields-name
slug: jsp-editor-imagebrowser-schema-model-fields-name
tags: api, java
publish: true
---

# \<kendo:editor-imagebrowser-schema-model-fields-name\>
A JSP tag representing Kendo Name.

#### Example
    <kendo:editor-imagebrowser-schema-model-fields>
        <kendo:editor-imagebrowser-schema-model-fields-name></kendo:editor-imagebrowser-schema-model-fields-name>
    </kendo:editor-imagebrowser-schema-model-fields>


## Configuration Attributes


### field `String`

The name of the field.

#### Example
    <kendo:editor-imagebrowser-schema-model-fields-name field="field">
    </kendo:editor-imagebrowser-schema-model-fields-name>



### parse `String`

Specifies the function which will parse the field value. If not set default parsers will be used.

#### Example
    <kendo:editor-imagebrowser-schema-model-fields-name parse="handle_parse">
    </kendo:editor-imagebrowser-schema-model-fields-name>
    <script>
        function handle_parse(e) {
            // Code to handle the parse event.
        }
    </script>



## Child JSP Tags
 
