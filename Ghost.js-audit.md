Dependo: https://dl.dropboxusercontent.com/u/531857/dependo_report3.html

![ghost.js dependency graph](http://f.cl.ly/items/03150X0f0P050C1c0E0K/Image%202013.08.24%2010%3A28%3A54.png)

## index.js

* access to express through `app()`
* `.doFilter()` for nav items in locals
* `.notifications` passed to locals
* `.settings()` - settings to be passed to the client or theme through locals
* `.paths()`
* `.initTheme()` - the only place this is called.. it really should never have been in ghost.js
* `.init()`
* `.config()`