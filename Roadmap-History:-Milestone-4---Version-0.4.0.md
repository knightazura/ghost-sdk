## Milestone 4 - Version 0.4.0 - December-ish

Milestone 4 resulted in version 0.4.0 of Ghost. 

[Open issues](https://github.com/TryGhost/Ghost/issues?milestone=3&page=1&state=closed)

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