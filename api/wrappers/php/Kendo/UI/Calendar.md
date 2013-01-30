---
title: Calendar
slug: php-Calendar
tags: api, php
publish: true
---

# \Kendo\UI\Calendar

A PHP class representing Kendo Calendar.


## Methods

### change
Fires when the selected date is changed
#### Parameters

##### $value `string|\Kendo\JavaScriptFunction`

#### Example - using string which defines a JavaScript function

    $calendar = new \Kendo\UI\Calendar();
    $calendar->change('function(e) { }');

#### Example - using string which defines a JavaScript name
    <script>
        function onChange(e) {
            // handle the change event.
        }
    </script>
    <?php
    $calendar = new \Kendo\UI\Calendar();
    $calendar->change('onChange');
    ?>

#### Example - using \Kendo\JavaScriptFunction

    $calendar = new \Kendo\UI\Calendar();
    $calendar->change(new \Kendo\JavaScriptFunction('function(e) { }'));

### culture `string`

Specifies the culture info used by the widget.


#### Example - using string
    $calendar = new \Kendo\UI\Calendar();
    $calendar->culture('value');

### dates `array`

Specifies a list of dates, which will be passed to the month template.


#### Example - using array
    $calendar = new \Kendo\UI\Calendar();
    $calendar->dates(new array());

### depth `string`

Specifies the navigation depth.


#### Example - using string
    $calendar = new \Kendo\UI\Calendar();
    $calendar->depth('value');

### footer `string`

Template to be used for rendering the footer. If false, the footer will not be rendered.


#### Example - using string
    $calendar = new \Kendo\UI\Calendar();
    $calendar->footer('value');

### format `string`

Specifies the format, which is used to parse value set with value() method.


#### Example - using string
    $calendar = new \Kendo\UI\Calendar();
    $calendar->format('value');

### max `date`

Specifies the maximum date, which the calendar can show.


#### Example - using date
    $calendar = new \Kendo\UI\Calendar();
    $calendar->max(new date());

### min `date`

Specifies the minimum date, which the calendar can show.


#### Example - using date
    $calendar = new \Kendo\UI\Calendar();
    $calendar->min(new date());

### month

#### Parameters

##### $value `\Kendo\UI\CalendarMonth|array`

Templates for the cells rendered in the "month" view.


#### Example - using \Kendo\UI\CalendarMonth

    $calendar = new \Kendo\UI\Calendar();
    $month = new \Kendo\UI\CalendarMonth();
    $content = 'value';
    $month->content($content);
    $calendar->month($month);

#### Example - using array

    $calendar = new \Kendo\UI\Calendar();
    $content = 'value';
    $calendar->month(array('content' => $content));

### navigate
Fires when navigate
#### Parameters

##### $value `string|\Kendo\JavaScriptFunction`

#### Example - using string which defines a JavaScript function

    $calendar = new \Kendo\UI\Calendar();
    $calendar->navigate('function(e) { }');

#### Example - using string which defines a JavaScript name
    <script>
        function onNavigate(e) {
            // handle the navigate event.
        }
    </script>
    <?php
    $calendar = new \Kendo\UI\Calendar();
    $calendar->navigate('onNavigate');
    ?>

#### Example - using \Kendo\JavaScriptFunction

    $calendar = new \Kendo\UI\Calendar();
    $calendar->navigate(new \Kendo\JavaScriptFunction('function(e) { }'));

### start `string`

Specifies the start view.


#### Example - using string
    $calendar = new \Kendo\UI\Calendar();
    $calendar->start('value');

### value `date`

Specifies the selected date.


#### Example - using date
    $calendar = new \Kendo\UI\Calendar();
    $calendar->value(new date());
