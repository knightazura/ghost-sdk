The Roadmap aims to set out when certain features will appear. It reduces in clarity the further we go into the future, and is constantly being added to as we move forward.

If you're just looking to find out whether a feature is likely to end up in core or not, then take a look at the [planned features page](https://github.com/TryGhost/Ghost/wiki/Planned-Features). It's just a list, but we're adding more detail to it as we go.

**Update:** In order to deliver 0.4 this year, we have decided to cull a large body of work and focus on closing the milestone. This includes culling all work to do with the App API. We are going to aim to deliver a shorter cycle for 0.5 which focuses solely on the App API, and all of the work around i18n and multi-user that was scheduled for 0.5 will now be moved to 0.6.

## Milestone 4 - Version 0.4.0 - December

Milestone 4 will result in version 0.4.0 of Ghost. This is the current milestone. 

[Open issues](https://github.com/TryGhost/Ghost/issues?milestone=3&page=1&state=open)

### Goals

This version focuses around the App API, import tools and adding functionality which has been heavily requested during the launch phases. 

Milestone 4 is the first milestone which is not only after the public launch, but also developed in the open allowing anyone to get involved. This means that Milestone 4 has a heavy focus on architecture, further improving the Ghost internals, making it easier to work with, and adding non-user-facing features that will help Ghost to grow new features quickly in the future.

We had also planned to make our Ghost Developer Tools, or the API for building Apps, available at the end of this milestone, so that developers can start building Apps to extend Ghost's functionality. This too required a focus on the Ghost internals and so has been moved to it's own project in 0.5.

There are also a number of important enhancements and features we want to add to the publishing experience, to reduce user frustration wherever possible.

### Apps

Getting Apps off the ground:
* ~~Proposal: Plugin Architecture Refactor~~ [~~#769~~](https://github.com/TryGhost/Ghost/issues/769)

### Publishing Experience

#### New Features

* ~~Post settings menu: published time~~ [~~#907~~](https://github.com/TryGhost/Ghost/issues/907)
* ~~Add a warning message when leaving the page with unsaved post content~~. [~~#1327~~](https://github.com/TryGhost/Ghost/issues/1327) (Solve data loss problem)
* ~~Featured posts~~: [~~#1111~~](https://github.com/TryGhost/Ghost/issues/1111), [~~#1112~~](https://github.com/TryGhost/Ghost/issues/1112) 
* ~~Static pages:~~ [~~#969~~](https://github.com/TryGhost/Ghost/issues/969), [~~#1329~~](https://github.com/TryGhost/Ghost/issues/1329), [~~Casper#39~~](https://github.com/TryGhost/Casper/issues/39)
    * ~~[BUG] Static page issues~~ [~~#1350~~](https://github.com/TryGhost/Ghost/issues/1350)   

#### UI Improvements

* Post Settings UX [#1351](https://github.com/TryGhost/Ghost/issues/1351) [TOP PRIORITY]
* ~~New cmd+enter shortcut to go to a new paragraph without modifying the current line~~ [~~#645~~](https://github.com/TryGhost/Ghost/issues/645)
* ~~Improve image uploader UI~~ [~~#1356~~](https://github.com/TryGhost/Ghost/issues/1356)
* ~~[BUG] Wrong notification on updating post~~ [~~#1368~~](https://github.com/TryGhost/Ghost/issues/1368)
* ~~[BUG] Allow multiple underscores like: _________~~ [~~#1113~~](https://github.com/TryGhost/Ghost/issues/1113)
* ~~[BUG] Markdown bug: no new line inserted when quotes are used~~ [~~#974~~](https://github.com/TryGhost/Ghost/issues/974)


### Architecture

Items which focus purely on the Ghost internals have been pulled out into their own category. Many of these are required in order to introduce required features and improvements.

* Static Asset Management [#1405](https://github.com/TryGhost/Ghost/issues/1405) [TOP PRIORITY]
* Cache Control Headers [#1470]https://github.com/TryGhost/Ghost/issues/1470)
* API Improvements
	* ~~API Unit Tests~~ [~~#1189~~](https://github.com/TryGhost/Ghost/issues/1189)
    * Refactor to use API for data access [#755](https://github.com/TryGhost/Ghost/issues/755) [TOP PRIORITY]
* Migration Refactor
    * Currently the amount of work required to do a database migration makes this prohibitively hard. The goal of this work is to make the whole system easier to understand. This is made up of a number of issues: 
        * ~~Create schema.js~~ [~~#1398~~](https://github.com/TryGhost/Ghost/issues/1398)
        * ~~Refactor migration~~ [~~#1399~~](https://github.com/TryGhost/Ghost/issues/1399) && [~~#1400~~](https://github.com/TryGhost/Ghost/issues/1400)

* Config & internal structure 
	* Ghost install in sub directory support [#527](https://github.com/TryGhost/Ghost/issues/527) [TOP PRIORITY] [IN PROGRESS]
    * Make it possible to require ghost as a module [#1326](https://github.com/TryGhost/Ghost/issues/1326) [IN PROGRESS]
    * Customisable Permalinks [#1395](https://github.com/TryGhost/Ghost/issues/1395) [TOP PRIORITY] [IN PROGRESS]
	* Standardise getting paths and abs URLs [#1390](https://github.com/TryGhost/Ghost/issues/1390) [IN PROGRESS]
    * [BUG] If the theme is missing, admin crashes [#981](https://github.com/TryGhost/Ghost/issues/981)
    * Connect.multipart() deprecation warning  [#1227](https://github.com/TryGhost/Ghost/issues/1227) [TOP PRIORITY]
    * BIG FAT ghost.js & index.js refactor [#360](https://github.com/TryGhost/Ghost/issues/360)

#### Testing

* ~~Infra: Run unit tests against sqlite and mysql~~ [~~#921~~](https://github.com/TryGhost/Ghost/issues/921)
* ~~Infra: Test Fixtures~~ [~~#362~~](https://github.com/TryGhost/Ghost/issues/362)
* ~~Add postgres build and allow it to fail.~~ [~~#1555~~](https://github.com/TryGhost/Ghost/pull/1555)
* ~~Infra: Code coverage~~ [~~#361~~](https://github.com/TryGhost/Ghost/issues/361)

### Miscellaneous

The following issues don't really fit into any other major Milestone 4 category, but are still scheduled to get done in 0.4.

* Automatic Update Available Notifications [#1464](https://github.com/TryGhost/Ghost/issues/1464)

#### Theme API

* ~~In {{excerpt}} convert new lines to spaces~~ [~~#531~~](https://github.com/TryGhost/Ghost/issues/531)
* ~~Added new helper to escape URIs called {{encode}}~~ [~~#1092~~](https://github.com/TryGhost/Ghost/pull/1092)
* ~~Create prefix and suffix attribute for {{tags}} helper~~ [~~#607~~](https://github.com/TryGhost/Ghost/issues/607)

#### Security Improvements

* Enhancement: Remove "Insecure Content" warning for backend over SSL [#1300](https://github.com/TryGhost/Ghost/issues/1300)
* ~~Replace cookieSession with session~~ [~~#1230~~](https://github.com/TryGhost/Ghost/issues/1230)

#### Accounts
* ~~Limit login attempts~~ [~~#499~~](https://github.com/TryGhost/Ghost/issues/499)
* ~~Improved password reset tool~~ [~~#1471~~](https://github.com/TryGhost/Ghost/issues/1471) [TOP PRIORITY]
* ~~Account redirects~~ [~~#1472~~](https://github.com/TryGhost/Ghost/issues/1472)
* ~~[BUG] Signing in and then pressing the back button takes you to /ghost/signin/ instead of /ghost/~~ [~~#596~~](https://github.com/TryGhost/Ghost/issues/596)


## Bug List

Bugs which don't fit into the categories above. PLEASE KILL THESE WITH FIRE.

* ~~Editing publish date of unpublished post yields JavaScript error~~ [~~#1332~~](https://github.com/TryGhost/Ghost/issues/1332)
* custom partial/pagination.hbs not cleared on theme switch [#1203](https://github.com/TryGhost/Ghost/issues/1203)

----------

## Milestone 5 - Version 0.5.0

### Apps & Import

Getting Apps off the ground:
* Lock down the App Boilerplate: <https://github.com/TryGhost/Ghost-App/issues>
* Ghost Apps & the Ghost Developer Tools [#1474](https://github.com/TryGhost/Ghost/issues/1474)
   * Ghost Developer Tools 'proxy' object for apps [#1478](https://github.com/TryGhost/Ghost/issues/1478)
   * API / data restrictions for apps / internal on settings model [#1473] (https://github.com/TryGhost/Ghost/issues/1473) [TOP PRIORITY]

##### Import Apps:

**Note** This section needs (and will shortly be receiving) an overhaul and should mostly be ignored in the short-term.

* Ghost Importer: UI love [#953](https://github.com/TryGhost/Ghost/issues/953) [TOP PRIORITY]
* Add "Delete All Content" Button [#1445](https://github.com/TryGhost/Ghost/issues/1445)
* importing a bad database that fails to import still imports content [#837](https://github.com/TryGhost/Ghost/issues/837)
* De-duplicate posts and tags in importer [#806](https://github.com/TryGhost/Ghost/issues/806)

### Features and refactors required for Apps

* Users: Roll out the ACL/Permissions system [#357](https://github.com/TryGhost/Ghost/issues/357)
* Utilize Transactions in Data Operations [#586](https://github.com/TryGhost/Ghost/issues/586)   

### Misc for 0.5

The following issues don't really fit in with the Milestone 5 focus on Apps, but are still scheduled to get done in 0.5.

* Theme API: make `{{nextpost}}` `{{prevpost}}` available to themes [#529](https://github.com/TryGhost/Ghost/issues/529)
* Ugly debug upgrade tool [#1260](https://github.com/TryGhost/Ghost/issues/1260)
* Add 'ghost' CLI tool for installing from npm [#1001](https://github.com/TryGhost/Ghost/issues/1001)

----------
## Milestone 6 - Version 0.6.0

Planned for Spring/Early Summer next year.

[Open issues](https://github.com/TryGhost/Ghost/issues?milestone=4&page=1&state=open)

This version will focus heavily on adding localisation, and more site features such as tag, user and archive pages. We'll also hopefully roll out the dashboard, and start work on multi-user features.

Milestone 0.6 Mini Projects:

##### Shortcuts
* Keyboard Shortcut Overhaul [#1463](https://github.com/TryGhost/Ghost/issues/1463)
* [BUG] Select Word Keyboard Shortcut doesn't work [#1275](https://github.com/TryGhost/Ghost/issues/1275)
* [BUG] markdown help popup is truncated on small screens [#1273](https://github.com/TryGhost/Ghost/issues/1273)

##### Scrolling
**Note:**  This section needs an overhaul

* Editor screen: Advanced scroll features [#22](https://github.com/TryGhost/Ghost/issues/22)
* Be smarter about how we line up markdown code with the live preview [#704](https://github.com/TryGhost/Ghost/pull/704)
* [BUG] Editor UI - Scroll events are not smooth [#481](https://github.com/TryGhost/Ghost/issues/481)
* [BUG] Editor scrolling gets stuck when typing lots of text [#535](https://github.com/TryGhost/Ghost/issues/535)
* [BUG] Fucked up scrolling behaviour when typing  [#958](https://github.com/TryGhost/Ghost/issues/958)


### Future Releases

See [planned features](https://github.com/TryGhost/Ghost/wiki/Planned-Features) for an idea of what will be happening.

### Past Milestones

#### Milestone 3 - Version 0.3.0 - Kickstarter release

See [0.3.0](https://github.com/TryGhost/Ghost/commits/0.3.0)

#### Version 0.3.1

Maintenance release, see [0.3.1](https://github.com/TryGhost/Ghost/commits/0.3.1)

#### Version 0.3.2 (12th Oct), followed by Public release (14th Oct)

Maintenance release, see [0.3.2](https://github.com/TryGhost/Ghost/commits/0.3.2)

#### History 

For more history, please see the [pre-release roadmap](https://github.com/TryGhost/Ghost/wiki/Pre-release-Roadmap)