---
title: View
slug: spa-view
publish: true
---
# View Overview

The **View** class instantiates and binds, and handles the events of a certain screen from the application. Event handling and data binding can be performed either through **MVVM** or **declarative data attribute initialization**.
The view content can be specified either as an HTML string, or by passing the id of the script element which contains the markup.
By default, the view wraps its content in a `div` element. The element type can be changed using the `tagName` configuration option.

## Creating a View from HTML String
    <script>
        var index = new kendo.View({
            content: '<span>Hello World!</span>'
        });
    </script>

## Creating a View from Script Template
    <script id="index" type="text/x-kendo-template">
        <span>Hello World!</span>
    </script>

    <script>
        var index = new kendo.View({
            content: 'index'
        });
    </script>

## Rendering View Contents

The view renders its contents using the `render` method, which accepts a jQuery selector (or object) in which the contents will be appended. Alternatively, the render method can be called without parameters in order to retreive the view element for manual insertion.
The view instantiates its content when rendered for the first time. This means that the view definitinons can be included in the HEAD of the document before the script templates are present, as long as the rendering is performed after (or in) the document `ready` event.

## Rendering View in a Container

    <div id="app"></div>

    <script>
        var index = new kendo.View({
            content: '<span>Hello World!</span>'
        });

        index.render("#app");
    </script>

## Appending View Element

    <div id="app"></div>

    <script>
        var index = new kendo.View({
            content: '<span>Hello World!</span>'
        });

        $("#app").append(index.render());
    </script>

The view contents are initialized when rendered for the first time - subsequent render calls will not re-instantiate the view element, but append it to the given container (if provided), or simply return a reference to the existing view element.

## MVVM Integration

## Removing/Destroing Views
