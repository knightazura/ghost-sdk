You can now use Ghost as a NPM module!

### UPDATE! 

The API for using Ghost as an NPM module is changing in **0.5.2**. 

Calling `ghost()` will no longer start an express server. If you have setup Ghost this way with Ghost <0.5.2 you will need to change the code that calls the module. The new API signature will be:

```
ghost().then(function (app) {
    app.start();
});
``` 

This documentation will be updated with more details closer to the release.

### Using Ghost as an NPM module

1.  Include Ghost as a dependency in your `package.json` file

  ```
"dependencies": {
      "ghost": "0.4.2"
}
  ```

2.  Run `npm install` to install Ghost.

3.  Include the Ghost module where desired and then invoke it to start ghost.

  ```
var ghost = require('ghost');
ghost();
  ```

At this point Ghost should be running!

## Further customizations

### Decide where the `content/` directory should exist

By default Ghost will use the `content/` directory that exists inside the module.  To modify where Ghost's `content/` directory should exist you can pass in a JSON object into the `ghost()` function.  For sake of easy maintenance you can also pass in a JSON file:

  ```
ghost({
  config: path.join(__dirname, 'config.js')
});
  ```

An example `config.js` is based off the [config.example.js](https://github.com/TryGhost/Ghost/blob/master/config.example.js).

The configuration property that changes the `content/` location is:

```
paths: {
  contentPath: path.join(__dirname, '/content/'),
}
```

Modify that to change where the `content/` directory should exist.

**NOTE**:  If you change the location of the `content/` directory Ghost expects to find the same directory structure that exists in the module.  To get started copy the [default content directory structure](https://github.com/TryGhost/Ghost/tree/master/content) as the basis for your custom `content/` location.