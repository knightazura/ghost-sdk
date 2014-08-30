[IntelliJ](http://www.jetbrains.com/idea/) is the recommended IDE for developing Ghost - whether you're working on core, themes, or plugins, IntelliJ has full support for Node.js and several other tools that Ghost makes use of.

IntelliJ is a fully-fledged IDE, you can use it for developing Java just as easily as JavaScript. It does have a little brother [WebStorm](http://www.jetbrains.com/webstorm/), which should [work just as well for Node.js](http://blog.jetbrains.com/webide/2011/11/webstorm-your-node-app/) :)


### Setting up a Project



### Plugins

Under settings (win) / preferences (mac) -> plugins -> browse repositories

Select and install Nodejs & Handlebars/Mustache plugins

### Keyboard / Mouse shortcuts

IntelliJ has awesome shortcuts, take some time to get to know them. 

Under settings (win) / preferences (mac) -> Keymap 

In the search/find box: Type 'go'

You'll see entries for `Declaration` and `Implementation` which allow you to click on variables/functions & take you to the declaration or implementation. These are super useful for JS. Learn them or reassign them to something you'll remember.

In the search/find box: Type 'usage'

Assign `Find usages` to something like Cmd/Ctrl + Button2 Click by right-clicking on it and choosing 'Add mouse shortcut'. Cmd/Ctrl + Button 2 click on any variable or function name will then open a find box with all usages of that variable/function. Depending on your preferences, you may find `Show usages` or `Find usages in file` to be useful instead or as well as `Find usages`

IntelliJ is a power tool - take some time to learn the keybindings and discover what they do!

### Run Configurations

http://stackoverflow.com/questions/17043484/grunt-debugging-from-webstorm/17452803#17452803

### Debugging

http://themespectre.com/ghost-development-and-debugging-in-webstorm-step-by-step/

### Toolbars and Menus

I prefer to have no toolbar (View -> Toolbar), and instead have just the navigation bar (View -> Navigation Bar) with the few buttons I use (mainly run/debug buttons) on the Navigation Bar Toolbar. 

Everything is configurable under:

Under settings (win) / preferences (mac) -> Menus and Toolbars

View -> Toolbar = Main Toolbar
View -> Navigation Bar = Navigation Bar + Navigation Bar Toolbar

By adding just the buttons you want to the Navigation Bar Toolbar you end up with one less row of 'stuff' under the File menu bar, and a bit more screen real estate.

### Databases

It is possible to connect IntelliJ to your SQLite3 databases. You need to enable the Database Support plugin first. Go to Preferences -> Plugins, search for 'database', and tick 'Database Support'. You will need to restart IntelliJ.

**Pro tip**: Use **Xerial**, not Zentus

* You need to be in the 'Database' tool window (View -> Tool Windows -> Database)
* Click the plus button -> Data Source -> SQLite3 -> Xerial
* Give it a name
* Find the database file in content/data
* Drop down the 'Driver files' arrow & click the install link
* Click Test connection, Apply, OK
* You may need to right click on your new data source and press 'synchronize'
* You can now navigate, query and edit your database directly in IntelliJ







