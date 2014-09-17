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
   * See also the request for supporting Markdown flavors in the list below
* Intercept image uploads to generate thumbnails/etc.
   * Will need a separate permission that doesn't belong to a model.
* Multilingual blogs
   * Each post could be annotated with an AppField `language` - would require post filtering by AppField value (only posts with app_field language = `en`)
* Add roles and authentication to frontend (described [here](https://ghost.org/forum/plugins/16275-viewer-reader-role/))
* Hook into saving/deleting of posts (observer pattern)

Quick List from looking around GitHub / Forum:

* Editor stuff
  * Hemmingway app
  * Markdown Flavors
  * Mathjax
  * Vim bindings
* Media
  * oEmbed
* Login
  * 2FA
  * OAuth / Google/FB logins
* Blog output
  * RSS with excerpt
  * Meta data
  * Reading time
  * bookmarklets
* Infra
  * 301 redirects
  * output flat files 

Places to go for inspiration:

* https://github.com/TryGhost/Ghost/search?q=app+territory&ref=cmdform&type=Issues
* https://ghost.org/forum/plugins/

----

## App Profiles

### Disqus App
Type: comments

Quite possibly the most frequent change made to Casper, or any other theme, is to add comments. Disqus has emerged as a clear favourite of all the services available for adding comments to your blog, already available as a built-in part of many themes.

An App for Disqus would allow users to add Disqus comments to their blog without having to touch theme files or code. The only unique piece of configuration for Disqus would be the shortname. Therefore a setting would be needed for users to enter this.

A Disqus App may also wish to provide a comment count, which themes can also use if it is available. 

As an advanced feature, the App may also wish to add an extra field for posts, so that users can turn comments on or off at a post level.

As an interim, until the `{{comments}}` helper becomes widely used, the theme might want to provide a checkbox allowing the user to 'force' comments - which the theme might use some other way.

#### Basic features (should be available in 0.5):
* I want to embed data into post.hbs, either via a filter, or via a helper.
* I want to have a settings page where users can enter their disqus code
* I want to provide a custom helper for comment_count on the blog frontend

#### Advanced features (may not become available until later):
* I want to display comment_count in the admin UI
* I want to provide post-level configuration for comments
* I want to register dashboard widgets

#### Lifecycle

* The app gets added to the filesystem and marked as active.
* This causes the app to be installed, which means that the custom 'shortname' setting is registered with the database with a default value of null. 
* Because the shortname is null, there should be no impact at this stage - filters and helpers are not registered.
* User visits the app settings screen, enters their shortname and presses save
* This causes the app to register its filters and helpers, as they are now usable.
* Any restarts of Ghost will cause the app to be reactivated, and activating will now trigger filters and helpers to be registered because the shortname is now present

