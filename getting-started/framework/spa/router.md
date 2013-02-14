---
title: Router
slug: spa-router
publish: true
---

# Router Overview

The **Router** class is responsible for tracking the application state and navigating between the application states.
The router integrates into the browser history using the fragment version of the url (`#page`), making the application states bookmarkable and linkable.
It is also used for programmatic navigation to a given state. A change event is exposed, suitable for authorization hooks.


## Router with a root route callback

    <script>
        var router = new kendo.Router();

        router.route("/", function() {
            console.log("/ url was loaded");
        });

        $(function() {
            router.start();
        });
    </script>

By default, if the URL fragment is empty (or not present), the "/" route callback will be executed. The `init` event handler will be executed regardless of the initial URL.

## Parameters

The router implements most of the (Ruby on Rails)[http://guides.rubyonrails.org/routing.html#non-resourceful-routes] routing formats, supporting bound parameters, optional segments, and route globbing.
The parsed parts of the URL are passed as parameters to the route callback.


### Parameter Parsing

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

### Optional Segments


### Route Globbing

## Navigation

## Missing Routes, Intercepting Navigation
