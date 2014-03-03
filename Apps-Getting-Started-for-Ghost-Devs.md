This guide is a description of the set of APIs and tools which are currently in a state of constant change as we work through the Ghost Apps project solidifying and standardising how things will work. This documentation exists so that those developers who are working on the project can keep up to date and are able to build demo Apps for the purpose of building & testing the App Platform. This is *not* intended as a guide for App developers just yet. We may scrap the whole lot and start again at any moment :wink:

----

**Note:** This has been updated for Ghost-App 0.0.2 - breaking changes 

----

### Creating

Ghost Apps are created by extending the Ghost-App boilerplate. 

Create a new folder in your `content/apps` folder, for now the folder name is your app name. Permitted characters: `a-z`, `0-9`, `_`, `-`.

Inside the folder, create a `package.json` and an `index.js` file.

`package.json` should include `version` and `dependencies`:

```
{
  "version": "0.x",
  "dependencies": {
    "ghost-app": "0.0.2",
  }
}
```

`index.js` should look like:

```
var App = require('ghost-app'),

    MyApp;

MyApp = App.extend({

    install: function () {},

    uninstall: function () {},

    activate: function () {},

    deactivate: function () {}

});

module.exports = MyApp;
```

#### Proxy

The proxy object is available inside any lifecycle function as `this.app` for example you could do the following in the activate method and see the title 'Welcome to Ghost' output on startup.

```
this.app.api.posts.read(1).then(function (post) {
    console.log(post.title);
});
```

#### Filters

Filters are available via the proxy, or via a special syntax as part of the app lifecycle:

```
MyApp = App.extend({
    filters: {
       ghost_head: 'handleGhostHead',
       ghost_foot: [9, 'handleGhostFoot']
    },
    handleGhostHead: function () {},
    handleGhostFoot: function () {}
});
```

The array syntax can be used to provide an optional priority, the default is 5.

### Installing

Open up your database, and add the name of your app to `activeApps` in the settings table. 

For example, if your app's folder name is `example-app`, the value of `activeApps` should be `["example-app"]`. Double quotes are required.

Once added, restart Ghost and your app will be installed & loaded.

### Changelog

0.0.2
- Removed `.App` from boilerplate signature
- Added new filter syntax inc using `deregister` instead of `unregister`
- Switched underscore to lodash

0.0.1 
Initial publish