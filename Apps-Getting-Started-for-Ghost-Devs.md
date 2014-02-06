This guide is a description of a set of APIs and tools which are constantly changing so that Ghost devs can get stuck in with building the App Platform. This is *not* intended as a guide for App developers. We may scrap the whole lot and start again at any moment :wink:

### Creating

Ghost Apps are created by extending the Ghost-App boilerplate. 

Create a new folder in your `content/apps` folder, for now the folder name is your app name. Permitted characters: `a-z`, `0-9`, `_`, `-`.

Inside the folder, create a `package.json` and an `index.js` file.

`package.json` should include:

```
"dependencies": {
    "ghost-app": "~0.0.1",
}
```

`index.js` should look like:

```
var App = require('ghost-app').App,

    MyApp;

MyApp = App.extend({

    install: function () {},

    uninstall: function () {},

    activate: function () {},

    deactivate: function () {}

});

module.exports = MyApp;
```

The proxy object is available inside any lifecycle function as `this.app` for example you could do the following in the activate method and see the title 'Welcome to Ghost' output on startup.

```
this.app.api.posts.read(1).then(function (post) {
    console.log(post.title);
});
```

### Installing

Open up your database, and add the name of your app to `activeApps` in the settings table. 

For example, if your app's folder name is `example-app`, the value of `activeApps` should be `["example-apps"]`. Double quotes are required.

Once added, restart Ghost and your app will be installed & loaded.

### Things that have already changed under your feet

> `var App = require('ghost-app').App`

^ the `.App` will be gone as soon as I publish the next version to npm