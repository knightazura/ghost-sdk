One of the questions we get asked the most is (when) will Ghost do X?

We have a list of features that we plan to implement which is as long as a gorilla's arm, and it's hard to communicate. This list attempts to quantify that list, detail the finer points where we know them, and will be expanded upon as it becomes clearer how a feature will fit into Ghost. 

If you're looking to figure out whether or not a feature will be implemented, the principles are:

- Is it a feature that is fundamentally core to publishing digital content? If yes, then it will probably be in Ghost core. E.g I18n, post scheduling, etc.
- Is it something so large and complex that other companies have entire teams and infrastructures dedicated to it? Then it will probably be provided through 3rd party integrations. E.g. Comments, and media management.
- Is it something that is only relevant to a small group, or for a short time? If yes, it's probably plugin territory. E.g. XML-RPC, Import tools

## Planned Projects

There are some bugs and features which clearly belong together as a group, and some which are dependent on each other. These have formed into natural projects that we are planning to complete in various milestones.

### Apps

Ghost Apps (plugins) is the next big project that we will take on. This includes tying down the boilerplate & tools which are available for building Ghost Apps in the Ghost-App repository, as well as introducing a vast toolset in the Ghost internals. The first steps will include the ability to install and activate an App via the Ghost UI, and introducing more access control so that Ghost users can be sure what a Ghost App is able to do. Ghost will have filter hooks added at various points, and we'll start to build the tools for working with 3rd parties and the dashboard. At this time it is intended that Ghost Apps will be the sole focus of the 0.5.

### Multi User

Multi User is a pretty sizeable project. Ghost is inherently multi-user under the bonnet, but the UI has been locked down to a single user because it adds a level of complexity to every feature in terms of security. As part of the multi-user (and also as part of the Apps project), Ghost will have a complete ACL layer added, so that it is possible to control users, roles and permissions across every action in the Ghost admin. We will also add a stronger focus on XSS protection and ensuring that users cannot cause problems for other users.
 

### i18n & l10n

### Markdown2

### Ghost Editor



## Feature List

Please note: This list is not complete and is being added to on a regular basis.

### Localisation
Note: Ghost core will contain the tools for making Ghost work in various languages, but the languages and settings specific to different languages will be provided via a 'language pack'.
* date localisation
* advanced character sets
* translatable admin
* post language
* multi-language blog posts

### Blog content creation
* Extended markdown features (Haunted Markdown)
* Preview uses theme styles
* Post SEO
* Featured posts
* Post scheduling
* Post queue
* Auto-save & offline
* Post cover / feature image
* Video embedding
* Version control
* Post custom data

### Admin UI
* Better Markdown support / behaviour when live previewing
* Editor -> Preview consistency
* Advanced editor scrolling
* Post list filtering and search
* Tag management

### Site structure
* Static Pages
* Tag pages
* Archives
* Search
* Navigation menu UI
* Different permalink structures
* Support for installing Ghost in a subdomain
* Sitemap & other SEO tools

### Users
* Multiple users
* User management screen
* User role and permission management
* User profile pages
* Multi-author
* Advanced publishing workflows

### Plugins & integrations
* Basic plugin API / structure
* Hooks for interacting with Ghost
* Database API
* Routing API
* Dashboard widget API
* Admin UI hooks
* Authentication tools for working with 3rd parties
* API tools for interacting with 3rd party APIs
* Importer hooks, & improved import workflow
* Importer plugin (for WP, Tumblr, Blogger, etc)
* Public API for Ghost using OAuth
* Integration options for analytics, comments, media etc

### Themes
* Advanced excerpts
* Multiple image sizes
* Feature / cover images
* Previous & next post
* Post lists on post pages - latest, related, etc

### Core / Infrastructure
* Support for requiring Ghost
* More modularisation
* Command line tools
* Support for no-SQL
* Upgrade/update tools
* Auto-discover themes and plugins

### Haunted Markdown and the Editor
* We plan to introduce [Haunted Markdown](https://github.com/TryGhost/Ghost/wiki/Haunted-Markdown) as an official 'flavor' of Markdown, see the [future of Markdown](https://github.com/TryGhost/Ghost/wiki/Future-of-Markdown) page for details.
* This includes a plan to completely overhaul the editor