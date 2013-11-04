## server.js

* access to express through `app()`
* `.doFilter()` for nav items in locals
* `.notifications` passed to locals, used in auth middleware & cleanNti
* `.settings()` - settings to be passed to the client or theme through locals
* `.paths()`
* ~~`.initTheme()` - the only place this is called.. it really should never have been in ghost.js~~
* `.init()`
* `.config().env`
* .dbHash - used as secret for sessions to invalidate on new db
* `ghost` is passed to loadCoreFilters, loadCoreHelpers and initTheme and I18n.load

**Thoughts on server.js usage of ghost**:
* `.app()` was a stupid idea and needs to go away
* inits and loads probably belong together / can be simplified
* `initTheme` being in ghost.js is wrong
* `.settings()`, `.config()`, `.paths()`, `.dbHash` are all 'global' properties - we should have one clear way to read them - see [#573](https://github.com/TryGhost/Ghost/issues/573)
* `.notifications` hould probably be their own model, but stored in memory rather than bookshelf
* `doFilter` is part of the plugin/theme API and should be a separate thing
* `ghost` shouldn't be passed around

## api.js

* `.dataProvider` to get access to models (should just include models?)
* `.notifications` 
* `.settings()`
* `.updateSettingsCache()`

**Thoughts on index.js usage of ghost**:

* `dataProvider` shouldn't be needed at all anymore I don't think?
* `notifications` should probably be their own model, but stored in memory rather than bookshelf
* settings/settingsCache/cachedSettingsRequestHandler should all be moved back onto the model itself along with stuff to deal with the ideas here: [#567](https://github.com/TryGhost/Ghost/issues/567)

## admin.js 
* `.dataProvider` to get access to models (should just include api)
* `.notifications` - push, and length neither of which should be necessary

**Thoughts on admin.js usage of ghost**:
* both of these should be fairly simple to get rid of

## frontend.js
* `.doFilter()` for filtering posts before they reach the frontend
* `.settings()`

**Thoughts on frontend.js usage of ghost**:

* `.doFilter()` should be part of a separate plugin/theme api thing
* `.settings()` also needs to become it's own thing somewhere

## plugins/loader.js
* `.paths()`
* passed to `plugin.activate()` and `plugin.install()` which is purely for API access

**Thoughts on plugins/loader.js usage of ghost**:

* This is one of the more awkward bits of code around the ghost object, mainly because of the duplicity between obtaining useful state (paths) and the API (should be separated) 
* It should be WAY easier to get hold of the set of paths
* The object passed to the plugin should be a theme/plugin API only

## tests

### ghost_spec.js

* This one's ok, need access to ghost to test it! Buuut the tests are pretty poor and only cover a fraction of certain bits of stuff that are in `ghost.js`

### server_helpers_index_spec.js

* requires `ghost` to pass to `helpers.loadCoreHelpers`

** Dependency Graphs **

Dependo: https://dl.dropboxusercontent.com/u/531857/dependo_report3.html

![ghost.js dependency graph](http://f.cl.ly/items/03150X0f0P050C1c0E0K/Image%202013.08.24%2010%3A28%3A54.png)

![ghost.js dependency graph 2](http://f.cl.ly/items/1T0V0p2Q172j2W0P0P32/Image%202013.08.24%2010%3A34%3A42.png)