### (when) will Ghost do X?

We have a list of features that we plan to implement which is as long as a gorilla's arm, and it is pretty hard to communicate. This list attempts to quantify that list, detail the finer points where we know them, and will be expanded upon as it becomes clearer how a feature will fit into Ghost, and the [roadmap](https://github.com/TryGhost/Ghost/wiki/Roadmap). 

### what makes it into Ghost core?

If you're looking to figure out whether or not a feature will be implemented, the principles are:

- Is it a feature that is fundamentally core to publishing digital content? If yes, then it will probably be in Ghost core. E.g I18n, post scheduling, etc.
- Is it something so large and complex that other companies have entire teams and infrastructures dedicated to it? Then it will probably be provided through 3rd party integrations. E.g. Comments, and media management.
- Is it something that is only relevant to a small group, or for a short time? If yes, it is probably app territory. E.g. XML-RPC, Import tools
- Is it something that can only be added in core? If yes, then it will be considered in terms of benefit vs complexity.

### where is the dashboard?

The dashboard is the most ambitious planned feature for Ghost. It is essentially an entire web application all on its own, supporting many many smaller web applications. It is going to take considerable time and resource to implement, however the dashboard will only provide value once it is possible to add apps to Ghost, and integrate with 3rd party services. 

As it stands, the Ghost project is concentrating on far more important and valuable features, such as delivering apps, multi-user, i18n and other often requested features. It is hoped that as the project grows, more people will join in and contribute to Ghost, but currently there are very few frontend developers involved in the project. The current idea is to plan the dashboard as a side project during 0.5, and to try to put together a team willing to work on it during 0.5 and 0.6. Keep an eye out on the [dev blog](http://dev.ghost.org) for more information about this. 

If this fails, then the dashboard will likely become the focus of the 0.8 or 0.9 milestone. We are committed to delivering the dashboard in time for Ghost v1.0 which is scheduled to land around the beginning of 2015.


## Planned Projects

There are some bugs and features which clearly belong together as a group, and some which are dependent on each other. These have formed into natural projects that we are planning to complete in various milestones.

### Apps

Ghost Apps (plugins) is the next big project that we will take on. This includes tying down the boilerplate & tools which are available for building Ghost Apps in the Ghost-App repository, as well as introducing a vast toolset in the Ghost internals. The first steps will include the ability to install and activate an App via the Ghost UI, and introducing more access control so that Ghost users can be sure what a Ghost App is able to do. Ghost will have filter hooks added at various points, and we'll start to build the tools for working with 3rd parties and the dashboard. At this time it is intended that Ghost Apps will be the sole focus of the 0.5 milestone.

### Multi User

Multi User is a pretty sizeable project. Ghost is inherently multi-user under the bonnet, but the UI has been locked down to a single user because it adds a level of complexity to every feature in terms of security. As part of the multi-user (and also as part of the Apps project), Ghost will have a complete ACL layer added, so that it is possible to control users, roles and permissions across every action in the Ghost admin. We will also add a stronger focus on XSS protection and ensuring that users cannot cause problems for other users. At this time it is intended that Multi User will be the main focus of the 0.6 milestone.
 

### Localisation / i18n 

Ghost is currently pretty much UK-based English-language only, and has barely any features to account for timezones, locales, languages, alphabets, keyboard layouts or anything else that isn't UTC/English in either the admin or in themes. Even the USA folks luck out, sorry! All this is set to change with full support for multiple locales and languages across the admin and your blog posts. Throughout the Ghost GitHub, support for all of these sorts of features is refered to as `i18n` (internationalisation), and this is scheduled to be done along with multi-user in milestone 0.6.

One feature which is particularly key, Timezone support, may be introduced in 0.5.


### Markdown2



### Ghost Editor


### Magazine


### Dashboard



## Feature List

Please note: This list is not complete and is being added to on a regular basis.

### Localisation
Note: Ghost core will contain the tools for making Ghost work in various languages, but the languages and settings specific to different languages will be provided via a 'language pack'.

* Timezone settings
* date localisation
* advanced character sets for fonts
* translatable admin
* post language
* multi-language posts

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
* More permalink structures
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
* Data API
* Routes API
* Files API
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

### Markdown2 and the Editor
* We plan to introduce [Haunted Markdown](https://github.com/TryGhost/Ghost/wiki/Haunted-Markdown) as an official 'flavor' of Markdown, see the [future of Markdown](https://github.com/TryGhost/Ghost/wiki/Future-of-Markdown) page for details.
* This includes a plan to completely overhaul the editor