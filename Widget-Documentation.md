#  Building The Widget

This documentation provides the information needed to build and customise widgets.

## HTML

### Basic Widget <a id="basicWidget"></a> 

This is a blank widget which can be modified to display any content.

Example:

```
<div class="widget-{name}">
    <section class="widget-content">
    	// Content here
    </section>
    <footer class="widget-footer">
        <span class="widget-title">{title}</span>
        <div class="widget-settings-toggle"></div> // If it needs a settings pane
    </footer>
</div>

```


### Number Widget

Number Widgets are intended to be Widgets which display mainly numeric data.

_**Note:** Widget variations are set in the [SCSS](#scss)_


##### Specific Markup:

* **Count:** is the overall numeric data total.
* **Sub:** is the difference in numeric data of a given time period. The `mark` element inside can take a  class of `up` or `down` to colour the main difference value.

Example:

```
<div class="widget-{name}">
    <section class="widget-content">
        <div class="info">
            <span class="count">9,392</span>
            <span class="sub"><mark class="up">+39</mark> high fives today</span>
        </div>
    </section>
    <footer class="widget-footer">
        <span class="widget-title">{title}</span>
        <div class="widget-settings-toggle"></div> // If it needs a settings pane
    </footer>
</div>

```

### Settings Pane

This Widget type is exclusively for the settings pane of an individual Widget. It works for all Widget sizes.

Simply apply the class `widget-settings` to the main Widget element and use the following HTML markup to build your settings pane.

Example:

```
<div class="widget-{name} widget-settings">
    <header class="widget-header">
        <span class="widget-title">{widget name} Settings</span>
        <div class="widget-settings-toggle close"></div>
    </header>
    <section class="widget-content">
        <label>
            <span class="title">{input title}</span> <input type="text" value="{value}"/>
        </label>
        // More labels if needed here
    </section>
    <footer class="widget-footer">
        <div class="widget-settings-toggle done"></div>
    </footer>
</div>

```



### Other Sizes

Available sizes:

* 1x2
* 2x1
* 2x2

Apply the class `widget-{width ratio}x{height ratio}` to your main Widget element.

This works for both basic and number widgets.

_**Note:** If `widget-2x2` is applied to a Number Widget the `font-size` automatically increases._

Example:

```
<div class="widget-{name} widget-{width ratio}x{height ratio}">
    <section class="widget-content">
    	// Content here
    </section>
    <footer class="widget-footer">
        <span class="widget-title">{title}</span>
        <div class="widget-settings-toggle"></div> // If it needs a settings pane
    </footer>
</div>

```

## SCSS <a id="scss"></a> 

Setting up a Widget could not be easier. Simply extend the widget variation needed.

### Basic Widget

```
.widget-{name} {
    @extend %widget;
    // Custom Styles
}
```

### Number Widget

```
.widget-{name} {
    @extend %widget-number;
    // Custom Styles
}
```

# Registering A Widget


## The Widget Model
The default Widget model:

```
title: "",
name: "",
author: "",
applicationID: "",
size: "",
content: {
    template: '',
    data: {
        number: {
            count: 0,
            sub: {
                value: 0,
                dir: "", // "up" or "down"
                item: "", // Example "handshakes"
                period: "" // Exmaple "this week"
            }
        }
    }
},
settings: {
    settingsPane: false,
    enabled: false,
    options: [{
        title: "ERROR",
        value: "Widget options not set"
    }]
}
```

### Breakdown
Items denoted with `*` are optional.

* `title`: Title of the Widget.
* `name`: The shortname / handle of the Widget, used in the class name etc..
* `author`: The author of the Widget.
* `applicationID`: A unique Widget indentifier in the format `com.<companyName>.<widgetName>`
* `size`*: Either `1x2`, `2x1` or `2x2`. It sets the default Widget size, normally `1x1`.

##### `content`

* [`template`](#templates): Is the target Widget template. For the default number Widget use `default/number`, for custom templates use `custom/{name of template}`.

###### `data`
This holds all the data for a Widget. The example above shows a Number Widget, however custom Widgets can have any properties and values set.

**`number`*** <a id="numberData"></a> 

* `count`: The overall numeric figure of the Number Widget.
* `value`:  is the difference in numeric data of a given time period.
* `dir`: The direction in the difference. Either `up` or `down`.
* `item`: The unit being measured, e.g. 'likes' or 'views'.
* `period`: The period of time, e.g. 'this week'.

##### `settings`*
The settings pane is optional, due to some Widgets not requiring settings. _Having settings in a Widget is recommended, as optional Widget sizes and other preferences will not be available without settings enabled._

* `settingsPane`: This is set to either `true` or `false`, depending if there is settings available to a Widget. _Highly recommended this is set to `true`.  To allow users to alter Widget sizes etc.._
* `enabled`*: Is set when the Widget settings are visible. _Recommended this is not set._

**`options`**

This an array of objects referring to the changable settings in the Widget.

* `title`: The title of the settings input.
* `value`*: The default value of the relative input. (This will be set to the last known settings if already changed.).

## Widget Templates <a id="templates"></a> 

All Widgets need a template specified in their respective Model. The default templates are either `default/blank` or `default/number` and custom templates are `custom/{name of template}`.

To provide data for default Number Widgets [see above](#numberData).


### Building Templates

Custom templates are snippets of [Handlebars](http://handlebarsjs.com/) markup, which are rendered into the `widget-content` section of the main [Widget Template](#basicWidget).

A quick example using the Ghost Time Widget.

**Example Widget Template**

Note the references to the Widget Model Data.
```
<header class="summary clearfix">
    <span class="day">{{content.data.day}}</span>
    <span class="weather">{{content.data.weather}}°</span>
</header>
<time>
    <span class="clock">{{content.data.time}}</span>
    <span class="date">{{content.data.date}}</span>
</time>
```

**Example Widget Model Data**

```
day: "Today",
weather: "12",
time: "12:42PM",
date: "Monday / March 5 / 2013"
```
