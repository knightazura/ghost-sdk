* [Roadmap History](#roadmap-history)
  * [Past Milestones](#past-milestones)
  * [Past Projects](#past-projects)
* [Pre Release Roadmap](#pre-release-roadmap)

# Roadmap History

## Past Milestones

#### Version 0.5 (11th August)

Release the API, Ember and Multi-User projects as Ghost 0.5

See [0.5.0](https://github.com/TryGhost/Ghost/commits/0.5.0)

#### Version 0.4.2

Maintenance release with many new features

See [Milestone History](https://github.com/TryGhost/Ghost/wiki/Roadmap-History:-Milestone-4---Version-0.4.0#version-042---theme-updates--major-fixes) or the [release post](http://blog.ghost.org/ghost-0-4-2-maintenance-release/)

#### Version 0.4.1 (30th Jan)

Maintenance release, see [0.4.1](https://github.com/TryGhost/Ghost/commits/0.4.1)

#### Milestone 4 - Version 0.4.0 (13th Jan)

See [Milestone History](https://github.com/TryGhost/Ghost/wiki/Roadmap-History:-Milestone-4---Version-0.4.0) or the [Release Notes](https://github.com/TryGhost/Ghost/wiki/Release-Notes:-0.4.0)

#### Version 0.3.3 (18th of Oct)

Maintenance & security release, see [0.3.3](https://github.com/TryGhost/Ghost/commits/0.3.3)

#### Version 0.3.2 (12th Oct), followed by Public release (14th Oct)

Maintenance release, see [0.3.2](https://github.com/TryGhost/Ghost/commits/0.3.2)

#### Version 0.3.1 (27th Sep)

Maintenance release, see [0.3.1](https://github.com/TryGhost/Ghost/commits/0.3.1)

#### Milestone 3 - Version 0.3.0 - Kickstarter release

See [0.3.0](https://github.com/TryGhost/Ghost/commits/0.3.0)

## Past Projects:

## API

### In master Q2 2014

See the [Epic](https://github.com/TryGhost/Ghost/issues/2124) for an overview of the project, what was required and why. Additionally, see the [issue backlog](https://github.com/TryGhost/Ghost/issues?labels=&milestone=19&page=1&state=open) to pick up issues and monitor progress.

#### Goals:

* To standardise the Ghost data API by introducing a standard format which closely matches JSON-API
* To introduce new API endpoints needed for Apps, Themes and other core parts of Ghost.
* To introduce permissions / access control across the entire API
* To produce structure documentation of each endpoint, the expected response and any errors that may result

## Ember

The Ghost Admin will be rewritten in Ember.js as a full client side SPA, consuming the Ghost data API. This is a dependency for all features which depend on UI changes. This project was started several weeks ago, but has been put on hold so that everyone can focus on the refactoring work to the API which is a dependency if the Ember admin is ever going to work. We should be back to this project before the end of April.

See the [Epic](https://github.com/TryGhost/Ghost/issues/2271) for an overview of the project, what is required and why. Additionally, see the [issue backlog](https://github.com/TryGhost/Ghost/issues?milestone=17&state=open) to pick up issues and monitor progress.

#### Goals

* To rebuild the entire Ghost admin in Ember.js
* To resolve as many UI bugs/issues as possible
* To create a framework for rapid development of user interfaces in Ghost
* To lay the groundwork to deliver significant improvements for mobile
* ?To introduce a more holistic solution for managing keyboard shortcuts?

## Multi-user

Ghost will get the option to add multiple users, with differing roles and permissions. 

#### Goals
* To make it possible to have a multi-user blog
* To ensure that the admin UI is safe from XSS and other security issues
* To improve the first run/install and introduction experience for users

---


## Milestone 4 Version 0.4.0

Milestone 4 resulted in version 0.4.0 of Ghost. 

[Closed issues](https://github.com/TryGhost/Ghost/issues?milestone=3&page=1&state=closed)

### Goals

Milestone 4 is the first milestone which is not only after the public launch, but also developed in the open allowing anyone to get involved. This means that Milestone 4 has a heavy focus on architecture, further improving the Ghost internals, making it easier to work with, and adding non-user-facing features that will help Ghost to grow new features quickly in the future.

We had also planned to make our Ghost Developer Tools, or the API for building Apps, available at the end of this milestone, so that developers can start building Apps to extend Ghost's functionality. This too required a focus on the Ghost internals and so has been moved to its own project in 0.5.

There are also a number of important enhancements and features we want to add to the publishing experience, to reduce user frustration wherever possible.

### Apps

Getting Apps off the ground:
* ~~Proposal: Plugin Architecture Refactor~~ [~~#769~~](https://github.com/TryGhost/Ghost/issues/769)

### Publishing Experience

#### New Features

* ~~Post settings menu: published time~~ [~~#907~~](https://github.com/TryGhost/Ghost/issues/907)
* ~~Add a warning message when leaving the page with unsaved post content~~. [~~#1327~~](https://github.com/TryGhost/Ghost/issues/1327) (Solve data loss problem)
* ~~Featured posts~~: [~~#1111~~](https://github.com/TryGhost/Ghost/issues/1111), [~~#1112~~](https://github.com/TryGhost/Ghost/issues/1112) 
* ~~Static pages:~~ [~~#969~~](https://github.com/TryGhost/Ghost/issues/969), [~~#1329~~](https://github.com/TryGhost/Ghost/issues/1329), [~~Casper#39~~](https://github.com/TryGhost/Casper/issues/39), [~~#1350~~](https://github.com/TryGhost/Ghost/issues/1350)   

#### UI Improvements

* ~~Post Settings UX~~ [~~#1351~~](https://github.com/TryGhost/Ghost/issues/1351) [TOP PRIORITY]
* ~~New cmd+enter shortcut to go to a new paragraph without modifying the current line~~ [~~#645~~](https://github.com/TryGhost/Ghost/issues/645)
* ~~Improve image uploader UI~~ [~~#1356~~](https://github.com/TryGhost/Ghost/issues/1356)
* ~~[BUG] Wrong notification on updating post~~ [~~#1368~~](https://github.com/TryGhost/Ghost/issues/1368)
* ~~[BUG] Allow multiple underscores like: _________~~ [~~#1113~~](https://github.com/TryGhost/Ghost/issues/1113)
* ~~[BUG] Markdown bug: no new line inserted when quotes are used~~ [~~#974~~](https://github.com/TryGhost/Ghost/issues/974)


### Architecture

Items which focus purely on the Ghost internals have been pulled out into their own category. Many of these are required in order to introduce required features and improvements.

* ~~Cache Control Headers~~ [~~#1470~~](https://github.com/TryGhost/Ghost/issues/1470)
* ~~API Improvements~~ [~~1249~~](https://github.com/TryGhost/Ghost/issues/1249), [~~#1189~~](https://github.com/TryGhost/Ghost/issues/1189), [~~#755~~](https://github.com/TryGhost/Ghost/issues/755)
* Migration Refactor
    * Currently the amount of work required to do a database migration makes this prohibitively hard. The goal of this work is to make the whole system easier to understand. This is made up of issues [~~#1398~~](https://github.com/TryGhost/Ghost/issues/1398), [~~#1399~~](https://github.com/TryGhost/Ghost/issues/1399) & [~~#1400~~](https://github.com/TryGhost/Ghost/issues/1400)

* Config & internal structure 
	* ~~Ghost install in sub directory support~~ [~~#527~~](https://github.com/TryGhost/Ghost/issues/527) 
    * ~~Make it possible to require ghost as a module~~ [~~#1326~~](https://github.com/TryGhost/Ghost/issues/1326)
    * ~~Customisable Permalinks~~ [~~#1395~~](https://github.com/TryGhost/Ghost/issues/1395)
	* ~~Standardise getting paths and abs URLs~~ [~~#1390~~](https://github.com/TryGhost/Ghost/issues/1390) 
    * ~~[BUG] If the theme is missing, admin crashes~~ [~~#981~~](https://github.com/TryGhost/Ghost/issues/981)
    * ~~Connect.multipart() deprecation warning~~  [~~#1227~~](https://github.com/TryGhost/Ghost/issues/1227) 

#### Testing
Vast improvements to Ghost's test suite include: running unit tests against sqlite, mysql [~~#921~~](https://github.com/TryGhost/Ghost/issues/921) and postgres (Allowed failure) [~~#1555~~](https://github.com/TryGhost/Ghost/pull/1555). Separating the test fixtures out from Ghost's installation fixtures [~~#362~~](https://github.com/TryGhost/Ghost/issues/362), proper tests for the API [~~#1189~~](https://github.com/TryGhost/Ghost/issues/1189) and adding a code overage tool [~~#361~~](https://github.com/TryGhost/Ghost/issues/361)

### Miscellaneous

The following issues don't really fit into any other major Milestone 4 category, but are still scheduled to get done in 0.4.

* Automatic Update Available Notifications [#1464](https://github.com/TryGhost/Ghost/issues/1464)

#### Theme API

* ~~In {{excerpt}} convert new lines to spaces~~ [~~#531~~](https://github.com/TryGhost/Ghost/issues/531)
* ~~Added new helper to escape URIs called {{encode}}~~ [~~#1092~~](https://github.com/TryGhost/Ghost/pull/1092)
* ~~Create prefix and suffix attribute for {{tags}} helper~~ [~~#607~~](https://github.com/TryGhost/Ghost/issues/607)

#### Security Improvements

* ~~Enhancement: Remove "Insecure Content" warning for backend over SSL~~ [~~#1300~~](https://github.com/TryGhost/Ghost/issues/1300)
* ~~Replace cookieSession with session~~ [~~#1230~~](https://github.com/TryGhost/Ghost/issues/1230)

#### Accounts
* ~~Limit login attempts~~ [~~#499~~](https://github.com/TryGhost/Ghost/issues/499)
* ~~Improved password reset tool~~ [~~#1471~~](https://github.com/TryGhost/Ghost/issues/1471) 
* ~~Account redirects~~ [~~#1472~~](https://github.com/TryGhost/Ghost/issues/1472)
* ~~[BUG] Signing in and then pressing the back button takes you to /ghost/signin/ instead of /ghost/~~ [~~#596~~](https://github.com/TryGhost/Ghost/issues/596)


## Bug List

Bugs which don't fit into the categories above. PLEASE KILL THESE WITH FIRE.

* ~~Editing publish date of unpublished post yields JavaScript error~~ [~~#1332~~](https://github.com/TryGhost/Ghost/issues/1332)
* ~~custom partial/pagination.hbs not cleared on theme switch~~ [~~#1203~~](https://github.com/TryGhost/Ghost/issues/1203)

----

## Version 0.4.2 - Theme Updates & Major fixes

### Q1 2014

The work towards Milestone 5 has already delivered significant new features, bug fixes, and awesome infrastructural changes that make Ghost easier to work with. At the same time, there is a very long way to go still before we can deliver 0.5, and that is being extended because of the switch-over to Ember. Therefore the Ghost team has decided to take advantage of being pre-1.0 and deliver a patch release with new features.

0.4.2 will deliver many of the theme changes that were planned for 0.5, and some that were planned for 0.6! It will also fix a number of particularly hairy bugs, and significant improvements to the editor.

Take a look at the [closed issue list](https://github.com/TryGhost/Ghost/issues?direction=desc&milestone=18&page=1&sort=created&state=closed) to see what will be in 0.4.2

**Tasks**:

* [x] Add `package.json` support for themes, providing theme developers with a simple way to define key data about their themes.
* [x] Develop the advanced `has` helper to provide more options for customising themes dependent on what data is available.
* [x] Add the much-awaited tag pages feature.
* [X] Introduce support for custom page and tag templates, allowing individual pages or tags to have a different templates.

### Other

**Goal**: Ghost 0.5 should significantly improve the ease of creating and customising a blog.

**Tasks**:

* [x] Improvements towards using Ghost as a module, publish to npm

----


# Pre Release Roadmap 

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
* Theme/plugin API stuff:
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


##[Version 0.3](https://github.com/TryGhost/Ghost/issues?milestone=2&state=open) - Kickstarter access - Est 16th September* 

[Planning WIP]

Version 0.3 will be released to all 5,236 KickStarter backers in mid September. As such we want to focus on user experience and making Ghost feel like a real blogging application. We also want to ensure at this point that Ghost is reasonably stable & feature rich.

With this in mind, for 0.3 we'd like to focus on the following key areas:

* Users
    * Whilst we'll prob stick with the single-admin-user-owns-all-the-things for now, we should work on making the ownership explicit by rolling out the ACL system across the admin.
    * Add the user UI so that the details of the admin user can be changed
    * Get the concept of post author rolled out across the admin and frontend
* Advanced post features
    * First and foremost this includes:
        * archive page
        * post tagging 
        * post SEO
        * Image uploads
    * Other potential features for this release include a simple RSS feed, search, comments (disqus), custom fields, editing permalinks etc, haunted markdown (image, video, small). We'll play it by ear and see which features we think are most important / we are able to fit in the release.
* 3rd Party Integrations
    * We need to start by designing the architecture behind 3rd party integrations & connecting various services for various tasks: sharing, liking, pulling data for dashboard widgets, and implementing services like comments which work on the blog. 
    * We need a set of core tools for authenticating and authorising with various schemes and for interacting with various kinds of API (most are REST or at least HTTP based)
    * Additionally, the dashboard needs love. We need to plan out how internal widgets will work too and for 0.3 we'd like to have the following widgets up and running:
       * Analytics
       * Twitter
       * Facebook
       * App.net
       * Internal
* Themes & Plugins
    * API
        * Roll out filters across the admin and api (see [Imagining Ghost Themes and Plugins](https://github.com/TryGhost/Ghost/wiki/Imagining-Ghost-Themes-and-Plugins))
        * Connect up with the tools for 3rd party services
        * Improvements and additions to helpers (kinda requires the advanced post features)
    * Installing/registering/loading
        * The UI for activating a plugin and theme 
        * Add the concept of package.json to themes & plugins
        * Add the ability to register custom filters and helpers from plugins and themes
* Internal - i.e all the things we need to do to ensure Ghost is awesome:
    * finishing the conversion of the admin UI to backbone
    * adding a build step for the masses of client scripts
    * sharing code between server and client where possible
    * refactoring bits we aren't happy with (like ghost.js)
    * improving unit test coverage for core inc adding unit tests for client
    * adding automated functional tests

#### Version 0.3 planning

* Interactions Epic: #268
* User Epic: #269
* Themes & Plugins Epic: #270
* Advanced post features Epic: #271

##[Version 0.4](https://github.com/TryGhost/Ghost/issues?milestone=3&state=open) - Public access - Est Early October
* Custom field image uploads
* Install
* Dynamic Menu (ui to edit single menu)
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