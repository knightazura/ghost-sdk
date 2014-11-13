### (When) will Ghost do X?

We have a list of features that we plan to implement which is as long as a gorilla's arm, and it is pretty hard to communicate. This page attempts to quantify that list, detail the finer points where we know them, and will be expanded upon as it becomes clearer how a feature will fit into Ghost, and the [roadmap](https://github.com/TryGhost/Ghost/wiki/Roadmap). 

### What makes it into Ghost core?

See: https://github.com/TryGhost/Ghost/wiki/What-makes-it-into-Ghost-core%3F

### Where is the dashboard?

The dashboard is one of the most ambitious planned feature for Ghost. It is essentially an entire web application all on its own, supporting many many smaller web applications. It is going to take considerable time and resource to implement, however the dashboard will only provide value once it is possible to add apps to Ghost, and integrate with 3rd party services. In short, it'll be ready when it's ready, but we are committed to delivering it before Ghost hits v1.0.

---

## Planned Projects

There are some bugs and features which clearly belong together as a group, and some which are dependent on each other. These have formed into natural projects that we are planning to complete in various milestones.

### Apps

Ghost Apps (plugins) has an almost limitless scope as a project. This includes tying down the boilerplate & tools which are available for building Ghost Apps in the Ghost-App repository, as well as introducing a vast toolset in the Ghost internals. The first steps will include the ability to install and activate an App via the Ghost UI, and introducing more access control so that Ghost users can be sure what a Ghost App is able to do. Ghost will have filter hooks added at various points, and we'll start to build the tools for working with 3rd parties and the dashboard. 

### Localisation / i18n 

Ghost is currently pretty much UK-based English-language only, and has barely any features to account for timezones, locales, languages, alphabets, keyboard layouts or anything else that isn't UTC/English in either the admin or in themes. Even the USA folks luck out, sorry! All this is set to change with full support for multiple locales and languages across the admin and your blog posts. Throughout the Ghost GitHub, support for all of these sorts of features is referred to as `i18n` (internationalisation).

### Ghost Editor

A project to redesign and rebuild the Ghost editor is planned to take place before we ship Ghost 1.0, replacing the current iteration with a new component which doesn't depend on different markdown interpretations, which is easily extensible and which works as well on mobile as it does on desktop.

### Dashboard

The Dashboard project encompasses creating the dashboard framework, building the default Widgets which live within it, and creating all of the tools needed for apps to register and define their own widgets. It is an advanced one-page javascript application all of its own, and will likely be built in Ember or Angular, rather than Backbone. The dashboard project is scheduled to be planned and begin during the 0.5 milestone, but is not expected to ship until later.

---

## Feature List

**Please note:** This is the original feature bucket list that we have had since day 1. The [public roadmap](https://trello.com/b/EceUgtCL/ghost-roadmap) contains an updated todo list which you can vote and comment on, and you can also add suggestions by posting in the [forum](https://ghost.org/forum/bugs-suggestions/17479-ghost-roadmap-got-a-great-idea/)

### Localisation

* Timezone settings 
* date localisation 
* advanced character sets for fonts 
* translatable admin 
* post language 
* multi-language posts 

### Blog content creation

* Extended markdown features
* Preview uses theme styles
* Post scheduling 
* Post queue 
* Auto-save & offline 
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

* Archives
* Search 
* Navigation menu UI
* More permalink structures
* Sitemap 
* Other SEO tools

### Users

* User role and permission management 
* Advanced publishing workflows

### Apps & integrations

* Basic app API / structure 
* App installation/activation/management 
* App settings 
* Hooks for interacting with Ghost
* Data API 
* Routes API 
* Files API 
* Dashboard widget API 
* Admin UI hooks
* Authentication tools for working with 3rd parties
* API tools for interacting with 3rd party APIs
* Importer hooks, & improved import workflow
* Importer app (for WP, Tumblr, Blogger, etc)
* Public API for Ghost using OAuth
* Integration options for analytics, comments, media etc
* Name, version, other info support via `package.json`

### Themes

* Debugging tools 
* Placeholder helpers for app filters
* Advanced excerpts 
* Retrieve image in multiple sizes/formats 
* Previous & next post available on single post
* Dynamic / query helpers - Post lists on post pages - latest, related, etc
* Head/foot js snippet support (code injection)

### Core / Infrastructure

* More modularisation 
* Command line tools 
* Upgrade/update tools 
* Auto-discover themes and apps 