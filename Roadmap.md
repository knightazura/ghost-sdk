**PLEASE NOTE:** 
* All dates mentioned here are estimates and are by no means definitive. 
* Version numbers are also estimates, we may or may not increment at these points.
* This is still a work in progress in terms of features, some may be added, others may be removed or delayed

# Summary
I’m pretty certain that this is going to be TLDR; for many people, so in summary:
* We are introducing a new 0.1.1 milestone which marks the point at which Ghost should be useful as a blog, this milestone replaces 0.2.0 for delivery mid-June.
* At 0.1.1 it will be required that every contributor to Ghost setup a blog using Ghost & write at least one post a week. It doesn’t need to be public, although we’d like access, and we’re not expecting works of literature, we just want all of the developers to be exercising the system regularly.
* 0.2.0 is still the point at which VIP KickStarter access will happen, and we are hoping to only push it back by 7 days

## [Version 0.1.0](https://github.com/TryGhost/Ghost/commit/17d421bfcc9a766ff1f09ca69677d7a6a978e885) - Initial Prototype - 11th May

The first version of Ghost was a prototype version opened up to a small group of contributors. It had:
divided the code into core and user content
* basic structure of admin vs frontend code mapped out inside of core
* very basic save, edit and list features for posts
* a single theme with very basic functionality
* a single plugin, hard-coded to load/not load
* some notion of hooks for themes & plugins. 

## [Version 0.1.1](https://github.com/TryGhost/Ghost/issues?milestone=5&state=open) - Deployed Ghost - 16th Jun

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

### Missing features required for 0.1.1
**Ghost:**
* basic deploy tools [#103](https://github.com/TryGhost/Ghost/issues/103)
* admin user safety (no default user, registration allows for creation of single admin) [#138](https://github.com/TryGhost/Ghost/issues/138)
* set published by & published at [#117](https://github.com/TryGhost/Ghost/issues/117)
* data model refinements [#101](https://github.com/TryGhost/Ghost/issues/101)
* data export & import [#115](https://github.com/TryGhost/Ghost/issues/115)
* upgrade plan (how to upgrade without harming db/data/images) [#139](https://github.com/TryGhost/Ghost/issues/139)
* settings used for frontend config (nice to have) [#112](https://github.com/TryGhost/Ghost/issues/112)

**Casper:**
* pretty / featured first post (note there will be no featured image)
* non working post footer stuff (share, what do you think) stuff should be removed
* use configured title / desc / image / logo [mostly done]



##[Version 0.2](https://github.com/TryGhost/Ghost/issues?milestone=1&state=open) - Developer access - 23rd Jun

The second version of Ghost is intended to be released to VIP KickStarter backers via weekly and nightly builds. This version should be the first version which is feature complete enough to be realistically used by folks to run a blog, and therefore will start to require some compatibility between versions. 


* Static menu (edit via filter only)
* Add & edit post
* Delete post
* Save settings
* Post list
  * Chronological  - REQUIRES ISSUES
  * Paginated
  * Filters  - REQUIRES ISSUES
  * Groups  - REQUIRES ISSUES
* Save & publish post 
* Theme API  - REQUIRES ISSUES
* Plugin API  - REQUIRES ISSUES
* Login 
* Logout
* Image upload  

##[Version 0.3](https://github.com/TryGhost/Ghost/issues?milestone=2&state=open) - Kickstarter access - Est 16th August* 

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