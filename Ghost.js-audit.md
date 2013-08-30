## index.js

* access to express through `app()`
* `.doFilter()` for nav items in locals
* `.notifications` passed to locals, used in auth middleware & cleanNti
* `.settings()` - settings to be passed to the client or theme through locals
* `.paths()`
* `.initTheme()` - the only place this is called.. it really should never have been in ghost.js
* `.init()`
* `.config().env`
* .dbHash - used as secret for sessions to invalidate on new db
* `ghost` is passed to loadCoreFilters, loadCoreHelpers and initTheme and I18n.load

**Thoughts on index.js usage of ghost**:
* `.app()` was a stupid idea and needs to go away
* inits and loads probably belong together / can be simplified
* initTheme being in ghost.js is wrong
* .settings(), .config(), .paths() .dbHash, .notifications are all 'global' properties - we should have one clear way to read them - see [#573](https://github.com/TryGhost/Ghost/issues/573)
* doFilter is part of the plugin/theme API
* ghost shouldn't be passed around

## api.js

* `.dataProvider` to get access to models (should just include models?)
* `.notifications` 
* `.settings()`
* `.updateSettingsCache()`

**Thoughts on index.js usage of ghost**:

* dataProvider shouldn't be needed at all anymore I don't think?
* notifications should probably be their own model, but stored in memory rather than bookshelf
* settings/settingsCache/cachedSettingsRequestHandler should all be moved back onto the model itself along with stuff to deal with the ideas here: [#567](https://github.com/TryGhost/Ghost/issues/567)

Dependo: https://dl.dropboxusercontent.com/u/531857/dependo_report3.html

![ghost.js dependency graph](http://f.cl.ly/items/03150X0f0P050C1c0E0K/Image%202013.08.24%2010%3A28%3A54.png)

![ghost.js dependency graph 2](http://f.cl.ly/items/1T0V0p2Q172j2W0P0P32/Image%202013.08.24%2010%3A34%3A42.png)