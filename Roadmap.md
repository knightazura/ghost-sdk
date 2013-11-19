The Roadmap aims to set out when certain features will appear. It reduces in clarity the further we go into the future, and is constantly being added to as we move forward.

If you're just looking to find out whether a feature is likely to end up in core or not, then take a look at the [planned features page](https://github.com/TryGhost/Ghost/wiki/Planned-Features). It's just a list, but we're adding more detail to it as we go.

## Milestone 4 - Version 0.4.0 - Early / mid December

Milestone 4 will result in version 0.4.0 of Ghost. This is the current milestone. 

[Open issues](https://github.com/TryGhost/Ghost/issues?milestone=3&page=1&state=open)

### Goals

This version focuses around the App API, import tools and adding functionality which has been heavily requested during the launch phases. 

Milestone 4 is the first milestone which is not only after the public launch, but also developed in the open allowing anyone to get involved. This means that Milestone 4 has a heavy focus on architecture, further improving the Ghost internals, making it easier to work with, and adding non-user-facing features that will help Ghost to grow new features quickly in the future.

We also plan to make our Ghost Developer Tools, or the API for building Apps, available at the end of this milestone, so that developers can start building Apps to extend Ghost's functionality. This too requires a focus on the Ghost internals.

There are also a number of important enhancements and features we want to add to the publishing experience, to reduce user frustration wherever possible.

### Apps & Import

Getting Apps off the ground:
* ~~Proposal: Plugin Architecture Refactor~~ [~~#769~~](https://github.com/TryGhost/Ghost/issues/769)
* Lock down the App Boilerplate: <https://github.com/TryGhost/Ghost-App/issues>
* Ghost Apps & the Ghost Developer Tools [#1474](https://github.com/TryGhost/Ghost/issues/1474)
   * Ghost Developer Tools 'proxy' object for apps [#1478](https://github.com/TryGhost/Ghost/issues/1478)
   * API / data restrictions for apps / internal on settings model [#1473] [TOP PRIORITY](https://github.com/TryGhost/Ghost/issues/1473) 

##### Import Apps:

**Note** This section needs (and will shortly be receiving) an overhaul and should mostly be ignored in the short-term.

* Ghost Importer: UI love [#953](https://github.com/TryGhost/Ghost/issues/953) [TOP PRIORITY]
* Add "Delete All Content" Button [#1445](https://github.com/TryGhost/Ghost/issues/1445)
* importing a bad database that fails to import still imports content [#837](https://github.com/TryGhost/Ghost/issues/837)
* De-duplicate posts and tags in importer [#806](https://github.com/TryGhost/Ghost/issues/806)
* [BUG] Data imported notification shows after I've logged in [#1452](https://github.com/TryGhost/Ghost/issues/1452)

### Publishing Experience

#### New Features

* Add a warning message when leaving the page with unsaved post content. [~~#1327~~](https://github.com/TryGhost/Ghost/issues/1327) (Solve data loss problem)
* Featured posts: [~~#1111~~](https://github.com/TryGhost/Ghost/issues/1111), [~~#1112~~](https://github.com/TryGhost/Ghost/issues/1112) 
* Static pages: [~~#969~~](https://github.com/TryGhost/Ghost/issues/969), [~~#1329~~](https://github.com/TryGhost/Ghost/issues/1329), [~~Casper#39~~](https://github.com/TryGhost/Casper/issues/39)
    * [BUG] Static page issues [#1350](https://github.com/TryGhost/Ghost/issues/1350)   
* SEO Improvements
	* Generate sitemap.xml [#623](https://github.com/TryGhost/Ghost/issues/623)
    * next and prev rel links in head [#685](https://github.com/TryGhost/Ghost/issues/685)
* Image features, including cover images and different sizes [#128] - more details soon
    * Ghost Image Output [#128](https://github.com/TryGhost/Ghost/issues/128) 

#### UI Improvements

* Post Settings UX [#1351](https://github.com/TryGhost/Ghost/issues/1351) [TOP PRIORITY]
* Responsive videos inside the Ghost editor [#1367](https://github.com/TryGhost/Ghost/issues/1367)
* Improve image uploader UI [#1356](https://github.com/TryGhost/Ghost/issues/1356)
* Set a sensible default sort order for post management admin [#1303](https://github.com/TryGhost/Ghost/issues/1303)
* [BUG] Wrong notification on updating post [#1368](https://github.com/TryGhost/Ghost/issues/1368)
* [BUG] Allow multiple underscores like: _________ [#1113](https://github.com/TryGhost/Ghost/issues/1113)
* [BUG] Markdown bug: no new line inserted when quotes are used [#974](https://github.com/TryGhost/Ghost/issues/974)

##### Scrolling
**Note:**  This section needs an overhaul

* Editor screen: Advanced scroll features [#22](https://github.com/TryGhost/Ghost/issues/22)
* Be smarter about how we line up markdown code with the live preview [#704](https://github.com/TryGhost/Ghost/pull/704)
* [BUG] Editor UI - Scroll events are not smooth [#481](https://github.com/TryGhost/Ghost/issues/481)
* [BUG] Editor scrolling gets stuck when typing lots of text [#535](https://github.com/TryGhost/Ghost/issues/535)
* [BUG] Fucked up scrolling behaviour when typing  [#958](https://github.com/TryGhost/Ghost/issues/958)

##### Shortcuts
* Keyboard Shortcut Overhaul [#1463](https://github.com/TryGhost/Ghost/issues/1463)
* [BUG] Select Word Keyboard Shortcut doesn't work [#1275](https://github.com/TryGhost/Ghost/issues/1275)
* [BUG] markdown help popup is truncated on small screens [#1273](https://github.com/TryGhost/Ghost/issues/1273)


### Architecture

Items which focus purely on the Ghost internals have been pulled out into their own category. Many of these are required in order to introduce required features and improvements.

* Static Asset Management [#1405](https://github.com/TryGhost/Ghost/issues/1405) [TOP PRIORITY]
* API Improvements
	* API Unit Tests [~~#1189~~](https://github.com/TryGhost/Ghost/issues/1189)
    * Refactor to use API for data access [#755](https://github.com/TryGhost/Ghost/issues/755)
	* API caching layer (enhancement) [#173](https://github.com/TryGhost/Ghost/issues/173)
    * More validation [#970](https://github.com/TryGhost/Ghost/issues/970)
    * Settings creation [#736](https://github.com/TryGhost/Ghost/issues/736)
* Migration Refactor
    * Create schema.js [#1398](https://github.com/TryGhost/Ghost/issues/1398)
    * Refactor migration (database not yet created) [#1399](https://github.com/TryGhost/Ghost/issues/1399)
    * Refactor migration (database is out of date) [#1400](https://github.com/TryGhost/Ghost/issues/1400)
    * Add validation to models using schema attributes [#1401](https://github.com/TryGhost/Ghost/issues/1401)
    * Migrations: Column modification [#601](https://github.com/TryGhost/Ghost/issues/601)
    * Utilize Transactions in Data Operations [#586](https://github.com/TryGhost/Ghost/issues/586)   
* Config & internal structure 
	* Ghost install in sub directory support [#527](https://github.com/TryGhost/Ghost/issues/527) 
    * Make it possible to require ghost as a module [#1326](https://github.com/TryGhost/Ghost/issues/1326)
    * Customisable Permalinks [#1395](https://github.com/TryGhost/Ghost/issues/1395) [TOP PRIORITY]
	* Standardise getting paths and abs URLs [#1390](https://github.com/TryGhost/Ghost/issues/1390)
    * Make the `content` directory configurable [#1364](https://github.com/TryGhost/Ghost/issues/1364)
    * [BUG] If the theme is missing, admin crashes [#981](https://github.com/TryGhost/Ghost/issues/981)
    * Connect.multipart() deprecation warning  [#1227](https://github.com/TryGhost/Ghost/issues/1227) [TOP PRIORITY]
    * BIG FAT ghost.js & index.js refactor [#360](https://github.com/TryGhost/Ghost/issues/360)
* [Draft] Refactor notifications  [#1454](https://github.com/TryGhost/Ghost/issues/1454)
    * [BUG] Data imported notification shows after I've logged in [#1452](https://github.com/TryGhost/Ghost/issues/1452)
    * [BUG] closing a few alert messages is ugly [#836](https://github.com/TryGhost/Ghost/issues/836)

#### Testing

* Performance tests  [#1392](https://github.com/TryGhost/Ghost/issues/1392)
* CasperJS tests for mobile interactions and views [#403](https://github.com/TryGhost/Ghost/issues/403)

### Miscellaneous

The following issues don't really fit into any other major Milestone 4 category, but are still scheduled to get done in 0.4.

* Automatic Update Available Notifications [#1464](https://github.com/TryGhost/Ghost/issues/1464)
* Ugly debug upgrade tool [#1260](https://github.com/TryGhost/Ghost/issues/1260)
* Add 'ghost' CLI tool for installing from npm [#1001](https://github.com/TryGhost/Ghost/issues/1001)
* Grunt deploy [#927](https://github.com/TryGhost/Ghost/issues/927)
* Consider switching to javascript:void(0) for hrefs [#916](https://github.com/TryGhost/Ghost/issues/916)
* Backbone: data binding libraries / tools? [#550](https://github.com/TryGhost/Ghost/issues/550)
* Theme API: make `{{nextpost}}` `{{prevpost}}` available to themes [#529](https://github.com/TryGhost/Ghost/issues/529)

#### Security Improvements

* Users: Roll out the ACL/Permissions system [#357](https://github.com/TryGhost/Ghost/issues/357)
* Enhancement: Remove "Insecure Content" warning for backend over SSL [#1300](https://github.com/TryGhost/Ghost/issues/1300)
* XSS
   * Investigate XSS filtering [#1378](https://github.com/TryGhost/Ghost/issues/1378) [TOP PRIORITY]
   * Upgrade validator to 2.*.* [#1379](https://github.com/TryGhost/Ghost/issues/1379)
   * [BUG] Editor title removing spaces [#1328](https://github.com/TryGhost/Ghost/issues/1328)
* Replace cookieSession with session [#1230](https://github.com/TryGhost/Ghost/issues/1230)
* Content Security Policy - Report only mode [#1267](https://github.com/TryGhost/Ghost/issues/1267)

#### Accounts
* Limit login attempts [#499](https://github.com/TryGhost/Ghost/issues/499)
* Improved password reset tool [#1471](https://github.com/TryGhost/Ghost/issues/1471)
* Account redirects [#1472](https://github.com/TryGhost/Ghost/issues/1472)
* [BUG] Signing in and then pressing the back button takes you to /ghost/signin/ instead of /ghost/ [#596](https://github.com/TryGhost/Ghost/issues/596)


## Bug List

Bugs which don't fit into the categories above. PLEASE KILL THESE WITH FIRE.

* Editing publish date of unpublished post yields JavaScript error [#1332](https://github.com/TryGhost/Ghost/issues/1332)
* /settings/user page buggy in firefox. [#1210](https://github.com/TryGhost/Ghost/issues/1210)
* custom partial/pagination.hbs not cleared on theme switch [#1203](https://github.com/TryGhost/Ghost/issues/1203)
* Select boxes look weird on Firefox [#1109](https://github.com/TryGhost/Ghost/issues/1109)
* Fancy quotes are borked [#534](https://github.com/TryGhost/Ghost/issues/534)

----------

## Milestone 5 - Version 0.5.0

Planned for early next year.

[Open issues](https://github.com/TryGhost/Ghost/issues?milestone=4&page=1&state=open)

This version will focus heavily on adding localisation, and more site features such as tag, user and archive pages. We'll also hopefully roll out the dashboard, and start work on multi-user features.

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