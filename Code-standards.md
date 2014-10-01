Good, clear and consistent code styles are pivotal in the success of any software project. Good use of style can reduce errors, consistency will enable us to work together efficiently. Ghost uses a combination of [JSHint](http://www.jshint.com/) and [JSCS](https://github.com/jscs-dev/node-jscs) to maintain consistent styles throughout the codebase which roughly emulate the strict style rules from JSLint.

## The rules:

You can find the rules in the codebase. The root directory contains both a [.jshintrc](https://github.com/TryGhost/Ghost/blob/master/.jshintrc) and [.jscsrc](https://github.com/TryGhost/Ghost/blob/master/.jscsrc) file. Please note that the `/core/client/` directory, which contains the client-side ember code for the admin panel has its own [.jshintrc](https://github.com/TryGhost/Ghost/blob/master/core/client/.jshintrc) file. Many modern IDE's are able to pick up on these files and lint your code for you as you go.

The basic rules are:

* `grunt lint` checks your code (`grunt validate` runs all tests).
* Indent with 4 spaces.
* Single quotes in JS.
* One var per function.
* Commas at the end.
* Max line length 120.
* Use unix line endings.
* Don't litter with new lines
* Document as you go.
* Write tests.

## Guidance

A few key points to bear in mind. See also the [Zen of Python](http://www.python.org/dev/peps/pep-0020/) as it applies equally to JavaScript & Ghost.

* **When coding, less is always more.** Write the least amount of code possible to solve just the problem at hand. 
* **Predicting the future is impossible.** Try to distinguish between anticipating potential future problems and potential future features. The former is usually good, the latter is usually bad.
* **Callbacks are great, but promises and deferreds are even better.** We are using [bluebird](https://github.com/petkaantonov/bluebird) to provide promise functionality. In the vast majority of cases this is preferred to using callbacks.
* **'exports' comes last.** Define the public API to your module at the very end of the file, even if it is a single function.
* **Functional programming is functional.** Functions should be small and single-purpose. Large variable lists are a sign your function does too much.

## Frontend development standards (HTML & CSS)

- 4 spaces for HTML & CSS indentation. Never tabs.
- Double quotes only, never single quotes.
- Use tags and elements appropriate for an HTML5 doctype (e.g., self-closing tags)
- Adhere to the [Recess CSS property order](http://markdotto.com/2011/11/29/css-property-order/).
- Always a space after a property's colon (.e.g, `display: block;` and not `display:block;`).
- End all lines with a semi-colon.
- For multiple, comma-separated selectors, place each selector on its own line.
- Use `js-` prefixed classes for JavaScript hooks into the DOM, and never use these in CSS as per [slightly obtrusive JavaSript](http://ozmm.org/posts/slightly_obtrusive_javascript.html)

For more in depth information please read [Mark Otto](http://github.com/mdo)'s excellent [Code Guide](http://github.com/mdo/code-guide)