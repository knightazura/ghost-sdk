Initial thoughts on how to get up and running when developing the Ember Ghost admin app.

Command line statements to run:

```
git checkout ember
grunt
grunt clean
grunt dev
```

URL of Ember admin: 127.0.0.1:2368/ghost/ember/

**If you're having issues:**

If you can't seem to get things to work I have a few suggestions:

1.  Delete your `bower_components` directory and then run:

  ```
grunt init
grunt
  ```
  And then run the commands at top.