---
title: Single-Page Application Overview
slug: spa-overview
publish: true
---
# Kendo Single Page Application Overview

Kendo Single-Page Application (sometimes abbreviated as SPA) is a set of classes which aim at simplifying the building rich client-side based web applications.
More information about the Single-page Application pattern can be found in the [respective Wikipedia article](http://en.wikipedia.org/wiki/Single-page_application).

The **Router** class is responsible for tracking the application state and navigating between the application states. The router integrates into the browser history using the fragment version of the url (`#page`), making the application states bookmarkable and linkable.
It is also used for programatic navigation.

The **View** and **Layout** classes are deal with the UI. UI Event handling and data binding can be performed either through **MVVM** or **declarative data attribute initialization**. The **Layout** has one or more **regions** which act as view containers.

## Getting Started

