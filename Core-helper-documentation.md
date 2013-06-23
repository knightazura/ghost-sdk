## `foreach`

By default the each helper in handlebars adds the private properties `@index` for arrays and `@key` for objects, which can be used inside the each loop. 

`foreach` extends this and adds the additional private properties of `@first`, `@last`, `@even`, `@odd`, `@rowStart` and `@rowEnd` to both arrays and objects. This can be used to produce more complex layouts for post lists and other content. For examples see below:

### `@first` & `@last`

The following checks through an array or object e.g posts and tests for the first entry.

    {{#foreach posts}}
        {{#if @first}}
            <div>First post</div>
        {{/if}}
    {{/foreach}}

Nested if example:

    {{#foreach posts}}
        {{#if @first}}
            <div>First post</div>
        {{else}}
            {{#if @last}}
                <div>Last post</div>
            {{/if}}
        {{/if}}
    {{/foreach}}

### `@even` & `@odd`

The following example adds a class of even or odd, which could be used for zebra striping content:

    {{#foreach posts}}     
            <div class="{{#if @even}}even{{else}}odd{{/if}}">{{title}}</div>
    {{/foreach}}

### `@rowStart` & `@rowEnd`

The following example shows you how to pass in a column argument so that you can set properties for the first and last element in a row:

    {{#foreach posts columns=3}}
        <li class="{{#if @rowStart}}first{{/if}}{{#if @rowEnd}}last{{/if}}">{{title}}</li>
    {{/foreach}}