---
title: editor-imagebrowser-schema-model-fields-size
slug: jsp-editor-imagebrowser-schema-model-fields-size
tags: api, java
publish: true
---

# \<kendo:editor-imagebrowser-schema-model-fields-size\>
A JSP tag representing Kendo Size.

#### Example
    <kendo:editor-imagebrowser-schema-model-fields>
        <kendo:editor-imagebrowser-schema-model-fields-size></kendo:editor-imagebrowser-schema-model-fields-size>
    </kendo:editor-imagebrowser-schema-model-fields>


## Configuration Attributes


### field `String`

The name of the field.

#### Example
    <kendo:editor-imagebrowser-schema-model-fields-size field="field">
    </kendo:editor-imagebrowser-schema-model-fields-size>



### parse `String`

Specifies the function which will parse the field value. If not set default parsers will be used.

#### Example
    <kendo:editor-imagebrowser-schema-model-fields-size parse="handle_parse">
    </kendo:editor-imagebrowser-schema-model-fields-size>
    <script>
        function handle_parse(e) {
            // Code to handle the parse event.
        }
    </script>



## Child JSP Tags
 
