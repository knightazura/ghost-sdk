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

### Multi-User

Multi User is a pretty sizeable project. Ghost is inherently multi-user under the bonnet, but the UI has been locked down to a single user because it adds a level of complexity to every feature in terms of security. As part of the multi-user (and also as part of the Apps project), Ghost will have a complete ACL layer added, so that it is possible to control users, roles and permissions across every action in the Ghost admin. We will also add a stronger focus on XSS protection and ensuring that users cannot cause problems for other users. At this time it is intended that Multi User will be the main focus of the 0.6 milestone.
 

### Localisation / i18n 

Ghost is currently pretty much UK-based English-language only, and has barely any features to account for timezones, locales, languages, alphabets, keyboard layouts or anything else that isn't UTC/English in either the admin or in themes. Even the USA folks luck out, sorry! All this is set to change with full support for multiple locales and languages across the admin and your blog posts. Throughout the Ghost GitHub, support for all of these sorts of features is refered to as `i18n` (internationalisation), and this is scheduled to be done along with multi-user in milestone 0.6.

One feature which is particularly key, Timezone support, may be introduced in 0.5.


### Markdown2

Markdown is a fabulous tool and it comes in many different flavours. Ghost intends to develop a JavaScript parser for markdown which pulls in the best features from the greatest flavors (like GFM and MultiMarkdown). The features and how they work will be tightly spec'd and unit tested, and will be called 'Markdown2'. The Markdown2 JS parser will be available both as a node module and a browser script, and will replace the use of Showdown in Ghost. 

### Ghost Editor

With the Markdown2 parser in place, we will overhal the Ghost Editor to use it in both the editor and preview windows, rather than using CodeMirror's parser in the editor and showdown in the preview. This should instantly irradicate all of the tiny bugs and inconsistencies across the two panes.

### Magazine

"Magazine" is the name of the project that is currently scheduled for milestone 0.8. It encompasses all the features you'd need to run a larger, magazine style blog, including scheduling/queuing posts, managing complex teams with advanced publishing workflows, and features for building magazine style themes.

### Admin overhaul

Ghost's current admin interface is build using Backbone, originally rendered server-side, but partially moved over to rendering client side. It is a half-way house and desperately needs love. We are planning a project to rebuild the admin interface, using one of many potential technologies such as Rendr, Ember, or Angular. This project isn't currently scheduled for a milestone, instead it will likely run as a side project starting in 0.5 and getting released in whatever milestone it is completed. 

### Dashboard

The Dashboard project encompasses creating the dashboard framework, building the default Widgets which live within it, and creating all of the tools needed for apps to register and define their own widgets. It is an advanced one-page javascript application all of its own, and will likely be built in Ember or Angular, rather than Backbone. The dashboard project is scheduled to be planned and begin during the 0.5 milestone, but is not expected to ship until later.


## Feature List

Please note: This list is not complete and is being added to on a regular basis. Each item has just a short title/description, and where possible, a project and/or milestone indicator. *future* means this item hasn't been sorted into a project/milestone yet, it does not necessarily mean that it will be delivered after everything else.

### Localisation

Note: Ghost core will contain the tools for making Ghost work in various languages, but the languages and settings specific to different languages will be provided via a 'language pack'.

* Timezone settings *0.5*
* date localisation *i18n/0.6*
* advanced character sets for fonts *i18n/0.6*
* translatable admin *i18n/0.6*
* post language *i18n/0.6*
* multi-language posts *future*

### Blog content creation

* Extended markdown features (Markdown2) *editor/0.7*
* Preview uses theme styles *editor/0.7*
* Post SEO *magazine/0.8*
* Post scheduling *magazine/0.8*
* Post queue *magazine/0.8*
* Auto-save & offline *editor/0.7*
* Post cover / feature image *magazine/0.8*
* Video embedding *future*
* Version control *future*
* Post custom data *apps/0.5*

### Admin UI

* Installation screen *other/0.5* 
* Better Markdown support / behaviour when live previewing *editor/0.7*
* Editor -> Preview consistency *editor/0.7*
* Advanced editor scrolling *editor/0.7*
* Post list filtering and search *editor/0.7*
* Tag management *editor/0.7*
* Admin overhaul *future*

### Site structure

* Tag pages *0.5*
* Archives *magazine/0.8*
* Search *magazine/0.8*
* Navigation menu UI *magazine/0.8*
* More permalink structures *importer/0.5*
* Sitemap & other SEO tools *future*

### Users

* Multiple users *multi-user/0.6*
* User management screen *multi-user/0.6*
* User role and permission management *multi-user/0.6*
* User profile pages *multi-user/0.6*
* Multi-author *magazine/0.8*
* Advanced publishing workflows *magazine/0.8*

### Apps & integrations

* Basic app API / structure *apps/0.5*
* App installation/activation/management *apps/0.5*
* App settings *apps/0.5*
* Hooks for interacting with Ghost *apps/0.5*
* Data API *apps/0.5*
* Routes API *apps/0.5*
* Files API *apps/0.5*
* Dashboard widget API *dashboard*
* Admin UI hooks *apps/0.5*
* Authentication tools for working with 3rd parties *future*
* API tools for interacting with 3rd party APIs *future*
* Importer hooks, & improved import workflow *importer/0.5*
* Importer app (for WP, Tumblr, Blogger, etc) *importer/0.5*
* Public API for Ghost using OAuth *apps/0.5*
* Integration options for analytics, comments, media etc *apps/0.5*
* Name, version, other info support via `package.json` *apps/0.5*

### Themes

* `has` helper *themes/0.5*
* Name, version, other info support via `package.json` *themes/0.5*
* Debugging tools *themes/0.5*
* Custom templates *themes/0.5*
* Placeholder helpers for app filters *themes/0.5*
* Advanced excerpts *magazine/0.8*
* Feature / cover images *magazine/0.8*
* Retrieve image in multiple sizes/formats *magazine/0.8*
* Previous & next post available on single post *magazine/0.8*
* Dynamic helpers - Post lists on post pages - latest, related, etc *magazine/0.8*
* Head/foot js snippet support *future*

### Core / Infrastructure

* Support for requiring Ghost *other/0.5*
* More modularisation *future*
* Command line tools *future*
* Support for no-SQL *future*
* Upgrade/update tools *other/0.5*
* Auto-discover themes and apps *future*