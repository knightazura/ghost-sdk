A place to collect ideas for apps and specifically things that the apps need to be able to do.

The idea here is to list a high level goal, and then document what API/[GDT](https://github.com/TryGhost/Ghost/wiki/Imagining-the-Ghost-Developer-Tools) features are needed to achieve it.

If you have an idea, please add it to the list no need to break it down into features!

* Embed analytics code into every page
   * Be able to filter ghost.head or ghost.foot (need renaming)
* Embed comments into posts / pages
   * Add configuration settings to the admin
   * Have access to a `{{comments}}` helper
* Modify RSS feeds
   * Be able to filter rss.feed and rss.item   
* Way to supply additional headers
   * Add `X-Content-Duration` for .ogg files for example. (see [http://expressjs.com/3x/api.html#res.set](http://expressjs.com/3x/api.html#res.set))
* Receive data via webhook to add new posts
   * Integration into IFTTT (compare https://ifttt.com/wordpress)
* Github project daily/weekly/release summary post
   * Use Github Webhooks ([git-at-me](https://github.com/jgable/git-at-me)) to compile a summary of commits/PR/issues for a specified time range
* Way to specify a path for receiving REST data
   * Have a server POST data to a ghost path that the app can then store and use (like usage statistics every 2 hours from a server)
* Hook into the login process to add 2FA
   * https://ghost.org/forum/plugins/877-two-factor-auth/
* Hook into existing routes
   * https://keen.io/blog/78561215787/how-to-install-keen-io-analytics-into-your-node-js-app
* Extend core helpers
   * It would be awesome to extend native helpers like `{{#has ..}}` to check for attributes in custom fields (`{{#has audio='true'}}`)
* Modify HTML before rendering from markdown
   * Could be used by syntax highlighters to recognise the extended fenced code blocks notation.
* Intercept image uploads to generate thumbnails/etc.
   * Will need a separate permission that doesn't belong to a model.
* Multilingual blogs
   * Each post could be annotated with an AppField `language` - would require post filtering by AppField value (only posts with app_field language = `en`)


Places to go for inspiration:

* https://github.com/TryGhost/Ghost/search?q=app+territory&ref=cmdform&type=Issues
* https://ghost.org/forum/plugins/