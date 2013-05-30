#  Building The Widget

This documentation provides the information needed to build and customise widgets.

## HTML

### Basic Widget

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

Simple apply the class `widget-settings` to the main Widget element and use the following HTML markup to build your settings pane.

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
