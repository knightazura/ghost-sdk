**PLEASE NOTE:** 
* All dates mentioned here are estimates and are by no means definitive. 
* Version numbers are also estimates, we may or may not increment at these points.
* This is still a work in progress in terms of features, some may be added, others may be removed or delayed

# Summary
I’m pretty certain that this is going to be TLDR; for many people, so in summary:

* We are introducing a new 0.1.1 milestone which marks the point at which Ghost should be useful as a blog, this milestone replaces 0.2.0 for delivery mid-June.
* At 0.1.1 it will be required that every contributor to Ghost setup a blog using Ghost & write at least one post a week. It doesn’t need to be public, although we’d like access, and we’re not expecting works of literature, we just want all of the developers to be exercising the system regularly.
* 0.2.0 is still the point at which VIP KickStarter access will happen, and we are hoping to only push it back by 7 days

## [Version 0.1.0](https://github.com/TryGhost/Ghost/commit/17d421bfcc9a766ff1f09ca69677d7a6a978e885) - Initial Prototype - Completed 11th May

The first version of Ghost was a prototype version opened up to a small group of contributors. It had:

* divided the code into core and user content
* basic structure of admin vs frontend code mapped out inside of core
* very basic save, edit and list features for posts
* a single theme with very basic functionality
* a single plugin, hard-coded to load/not load
* some notion of hooks for themes & plugins. 

## [Version 0.1.1](https://github.com/TryGhost/Ghost/issues?milestone=5&state=open) - Deployed Ghost - Completed 18th Jun

In order to ensure that the code we are delivering in the 0.2.0 milestone meets requirements, we’re introducing a new milestone: 0.1.1

At version 0.1.1 it should be possible for any of the core developers to run Ghost as a public blog. It may be missing key features which one would expect from a blog, but it should be stable and safe in terms of future updates.

At this point, we want all contributors to deploy and run Ghost as a blog somewhere, and publish something at least once per week. It doesn't have to be public or prolific, but it's important that we test the code by having it running in real-world environments and being used in real world situations.

### Expected features for 0.1.1
A core dev should be able to (this means editing config files, or replacing images manually is acceptable but not desired):

* setup and run a blog
  * there should be some means to deploy a blog on ec2/nodejitsu/appfog or somewhere 
  * it should be easy to run the blog in such a way that is stable and long-running.
  * configure an admin level user & login/out as that user
* configure the blog to look like it belongs to them, this includes setting through any means:
  * title
  * description
  * logo
  * icon
* create, edit and publish a text-based blog post
  * start a new post, save it as a draft which is not shown on the front end
  * edit draft and published posts & save the changes
  * publish draft post so it becomes visible on the frontend
  * no fancy image upload in the preview, images can be added by using standard markdown
* have their homepage display a list of published posts ordered by publish date
  * displays their configured title / desc 
  * shows a list of n posts
  * only published posts should be shown
  * most recently published post should be first
* have each post link to a post page which displays the post
  * clicking on any post in the home page should take you to a single post page
* backup their blog before doing an upgrade to a new version
  * possible to export (and import) all data as JSON
  * maybe have a grunt task to zip & store the custom content

##[Version 0.2](https://github.com/TryGhost/Ghost/issues?milestone=1&state=open) - Developer access - Completed 11th July

The second version of Ghost is intended to be released to VIP KickStarter backers via weekly and nightly builds. This version should be the first version which is feature complete enough to be realistically used by folks to run a blog, and therefore will start to require some compatibility between versions. 

### Expected features for 0.2.0:
Any developer should be able to (this means there is a UI or tool provided and documented):

* download the code from a secure location, using their KS email address
* setup and run a blog
  * there should be some simple means to deploy a blog onto a platform, and growing/improving documentation on how to deploy it elsewhere.
  * it should be easy to run the blog in such a way that is stable and long-running.
* create themselves an admin user
  * Single admin user registration
  * Can login and logout
  * Admin user owns all the things
* configure their blog’s frontend settings via the settings panel
  * title
  * description
* create and edit blog posts
  * start a new post, save it as a draft which is not shown on the front end
  * edit draft and published posts & save the changes
  * publish draft post so it becomes visible on the frontend
* delete any post
  * post can be deleted from the manage posts screen
* transition post to published
  * post is marked as published
  * post is given published at & published by properties
  * from this point on, post appears in frontend, correctly ordered by its published date
  * there is no scheduling available yet.
  * a post can be unpublished
* have their homepage display a list of published posts ordered by publish date
  * displays their configured title / desc
  * shows a list of n posts
  * only published posts should be shown
  * most recently published post should be first
  * pagination should be available to view older posts
* [TODO: finish tying down theme/plugin API stuff]
  * Theme API basics
    * Static menu 
  * Plugin API basics

### Architectural Requirements
* Users / ACL - we will begin with the concept of a single admin user who has all permissions 
* Admin frontend - should be converted fully to Backbone
* Function wrappers removed from node code
* Ghost.js cleanup

### Additional requirements
In addition to features, we have the following requirements if it is to be possible for us to realistically run Ghost as a blog.

* Stability 
  * Ghost shouldn’t crash unexpectedly
  * We need to be reasonably certain that we are using error handling where necessary
* Well-tested 
  * Ghost should have been running, as a blog, at several locations
  * We should have as much test coverage as possible
* Upgradable & data safe 
  * we need to be able to, at the bare minimum, export post data before an upgrade incase we break something terrible & lose data
  * we will need a plan for how to upgrade Ghost without overwriting data, custom images, custom themes and custom plugins


### Notes on compatibility from 0.2.0 onward:
we will have to manage database changes through migrations, meaning tying down the data model is a high priority
any filters in place must continue to work in the same or similar way
features should not be removed

*We will have breaking changes, there is little doubt, but these will require a version bump*


##[Version 0.3](https://github.com/TryGhost/Ghost/issues?milestone=2&state=open) - Kickstarter access - Est 16th August* 

Version 0.3 will be released to all 5,236 KickStarter backers in mid August. As such we want to focus on user experience and making Ghost feel like a real blogging application. We also want to ensure at this point that Ghost is reasonably stable.

With this in mind, for 0.3 we'd like to focus on the following key areas:

* Users
	* Whilst we'll prob stick with the single-admin-user-owns-all-the-things for now, we should work on making the ownership explicit by rolling out the ACL system across the admin.
    * Add the user UI so that the details of the admin user can be changed
    * Get the concept of post author rolled out across the admin and frontend
* Advanced post features
	* First and foremost this includes an archive page, post tagging and post SEO. 
    * Other potential features for this release include a simple RSS feed, image uploads, search, comments, custom field, scheduling, haunted markdown. We'll play it by ear and see which features we think are most important.
* Theme & Plugin API
	* Roll out filters across the admin and api (see [Imagining Ghost Themes and Plugins](https://github.com/TryGhost/Ghost/wiki/Imagining-Ghost-Themes-and-Plugins)
    * Improvements and additions to helpers (kinda requires the advanced post features)
* Theme & Plugin installing/registering/loading
	* The UI for activating a plugin/theme will probably not be in this version
    * Add the concept of package.json to themes & plugins
    * Add the ability to register custom filters and helpers from plugins and themes
    
* Internal - i.e all the things we need to do to ensure Ghost is awesome:
	* finishing the conversion of the admin UI to backbone
    * adding a build step for the masses of client scripts
    * sharing code between server and client where possible
	* refactoring bits we aren't happy with (like ghost.js)
    * improving unit test coverage for core inc adding unit tests for client
    * adding automated functional tests
    
    


What we were originally planning would be in 0.3

* Image upload
* Dynamic Menu (ui to edit single menu)
* Archives (Casper)
* Edit single user
* Basic RSS feed
* Dashboard
  * Analytics
  * Twitter
  * Facebook
  * App.net
  * Internal
* Tags on posts
* Search
* Install
* Haunted Markdown
  * image
  * video
  * small
* Comments (disqus)

##[Version 0.4](https://github.com/TryGhost/Ghost/issues?milestone=3&state=open) - Public access - Est 2nd September
* Schedule post
* Mobile UI + Interactions
* Importer
  * WordPress
  * Tumblr
  * Blogger
* Pages


##[Version 0.5](https://github.com/TryGhost/Ghost/issues?milestone=4&state=open) - ? - Est 16th December
* Version control / revisions
* RSS & Pubsubhubbub
* Dashboard
  * full set (initial...)
* Post queue
* Auto save + offline
* User management
* Haunted markdown (full basic...)
* Share to... 
  * Twitter
  * Facebook
  * ADN
* Theme-styled markdown/editor preview

##Future Release
* Public API
* User roles
* Multi Author
* Upgrade to MySQL/PostGres
* Switch to NoSQL
* Advanced publish workflows