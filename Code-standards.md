[Work in progress]

Good, clear and consistent code styles are pivotal in the success of any software project. Good use of style can reduce errors, consistency will enable us to work together efficiently. As there is an element of personal preference in style, I am certain that some people will not be happy with the code standards I've put into place. If this is the case for you, I ask that you take half an hour to listen to the first half of [Crockford on JavaScript - Section 8: Programming Style & Your Brain](http://www.youtube.com/watch?v=taaEzHI9xyY&feature=youtube_gdata_player) to help understand why I've made these choices.

## The rules:

* JSLint is King (see JSLint section below). 
* Use strict mode
* Protect the global scope
* Indent with 4 spaces
* Max line lenght 120
* Use unix line endings
* Document as you go - we are using groc and jsdoc formats
* Write tests, unit tests are in nodeunit, functional using casperjs

##Guidance

A few key points to bear in mind. See also the [Zen of Python](http://www.python.org/dev/peps/pep-0020/) as it applies equally to JavaScript & Ghost.

* **When coding, less is always more.** Write the least amount of code possible to solve just the problem at hand. 
* **Predicting the future is impossible.** Try to distinguish between anticipating potential future problems and potential future features. The former is usually good, the latter is usually bad.
* **Callbacks are great, but promises and deferreds are even better.** We are using ### library to provide promise functionality. In the vast majority of cases this is preferred to using callbacks.
* **'exports' comes last**
Define the public API to your module at the very end of the file, even if it is a single function.
* **Functional programming is functional** Functions should be small and single-purpose. Large variable lists are a sign your function does too much


## JSLint

All code (3rd party libraries not included) must pass JSLint with the exception of the dangling underscore rule, please see the section on 'Use of Underscores' for more details. Your IDE should have some configuration settings for enabling/disabling different rules. You can turn off the dangling/trailing underscore rule using "/*jslint nomen: true */", in IntelliJ (my IDE of choice) by checking "dangling _ in identifiers" and in Sublime Text 2 you need the --nomen option.

Please note: JSHint is not the same as JSLint out of the box, the rules are different and consistency is very important. If you are using JSHint, please make sure your options match those of JSLint.


####Problems you may run into with JSLint

Express and some of the other libraries we will use have made use of
reserved keywords in their API's. JSLint will not like this. The
solution is to use array syntax, rather than dot notation in these
cases.

For details of all the various JSLint errors and what they mean, please see [JSLint Error Explanations](http://jslinterrors.com/)

##Use of underscores

Dangling underscores are permitted to allow for the following use cases:

* using the underscore library
* naming function arguments which have the same name as an externally scoped variable

Please do not use underscores to denote private properties or methods.

```
_ = require("underscore")
_.each()
```
OK

```
var myObj = function () {
    var name;
    this.setName = function (_name) {
        name = _name;
    }
};
```
OK

```
var myObj = function () {
    var _name;
    this.setName = function (name) {
        _name = name;
    }
};
```
NOT OK