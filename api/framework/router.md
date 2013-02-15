---
title: kendo.Router
slug: framework-kendo.router
tags: api,framework
publish: true
---

# kendo.Router

## Methods

### start

Activates the router binding to the URL fragment part changes.

### Example

    <script>
        var router = new kendo.Router();

        $(function() {
            router.start();
        });
    </script>

### route

Specifies a callback for the given route. The route definition can contain **bound parameters**, **optional segments**, and **route globbing**.
The parsed parts of the URL are passed as parameters to the route callback.

### Parameters

#### route `String`

The route definition.

#### callback `Function`

The callback to be executed when the route is matched.

### Example

    <script>
        var router = new kendo.Router();

        router.route("/items/:category/:id", function(category, id) {
            console.log(category, "item with", id, " was requested");
        });

        $(function() {
            router.start();

            // ...

            router.navigate("/items/books/59");
        });
    </script>

### navigate

### destroy

## Events

### change

### routeMissing


