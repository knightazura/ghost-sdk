The Ghost Developer Tools (GDTs) are a set of APIs which allow developers to build apps on top of the Ghost platform.

Communicating the vision for something as broad and all-encompassing as the plan we have for the Ghost Developer Tools is a difficult task. This document attempts to explain the ideas we have for how it should work and how the different parts fit together.

These apps can do many things, from making minor adjustments to the functionality of a Ghost blog, to building integrations with 3rd party services, to (if you really want to) extending the Ghost Platform into something much more than just a blog.


## Principles

The GDTs adhere to the following principles:

* consistency, consistency, consistency
* providing 1 clear way to do things
* minimal boilerplate
* sensible, manageable structure
* defined interface guidelines 
* easily extensible
* secure, safe, and dependable

Essentially, the core should provide the tools for apps to use in creative ways. The tools provide power and flexibility to be used in ways we cannot imagine - pretty much anything should be possible. Any restrictions should exist only where it serves the GDT principles or protects the core of Ghost. 

### Apps should not

* Do anything illegal
* Compromise the security or integrity of a Ghost blog
* Compromise user data or privacy
* Do anything to damage the Ghost brand or trademark


## App fundamentals

The first principle of creating a Ghost app is creating consistency in the code and in the end user experience. To do this, all apps will start out with a set of meta data provided through a package.json file, including a name, description, keywords, an icon etc.

The Ghost admin panel will have an Apps screen displaying any installed apps, much like you might see on a mobile OS. Each app will have a name and be represented by an icon. Clicking on an app will take you to a management or settings page for that application. Every application will have its own screen, and this is the only place where an app will be able to provide settings.

Apps will be able to register other entities which may be managed elsewhere, such as widgets for the dashboard, accounts for 3rd party services, custom post data, embeddable content etc. With each type of thing having its own consistent location in the UI.

A key example of how all this will work is dashboard widgets. A button on the dashboard will take you to a list of available widgets, whether they are part of core or provided by an app. A widget can be added to the dashboard, and then customised with its own set of settings. Widgets can be dragged around, resized and removed from the dashboard.

The GDTs will provide the tools for registering a widget and then defining its content, interactions, available sizes and settings in the most straightforward way possible whilst maintaining all the flexibility of effectively providing a mini-app all in itself.


## The toolkit

Some of individual APIs and tools that we intend to provide include:

- Ghost (data) API, for making requests to the Ghost data layer, also allows for defining data to be stored
- Filters API, for hooking directly into Ghost functionality
- Theme API, for providing custom handlebars helpers & other theme-specific tools
- Widget API, for creating dashboard mini-apps
- Services API, for managing accounts/credentials for 3rd party services
- Routes API, for adding custom routes
- Files API, for hooking into and overriding how Ghost stores files
- UI Tools, for adding to the Ghost admin UI
- Auth Tools, for autenticating with 3rd parties
- API Tools, for sending and receiving data from 3rd party APIs
- Asset Management tools, for defining custom js, css, and images for your app
- Templating tools, so apps can define hbs templates making use of helpers
- i18n tools, so apps can hook into all the language, date and other i18n/l10n tools in Ghost core

It's pretty huge, and it is all going to start out pretty basic, and build in complexity and power over time.

### Little recommendations for budding app (and theme) developers

The GDT is intended to provide powerful tools that developers can use in creative ways to modify and build on top of in creative ways. We ask that developers be responsible, and do not abuse these powers.

If you build an app or theme which uses an unintended bug/feature please do 1) tell us about it and 2) expect it to go away at some point breaking your app / theme - where possible we'll try to replace it with something intended for the purpose.

If you build an app which implements a feature exactly as it is planned on the Ghost roadmap, you do so at your own behest. We highly recommend instead being the person that commits the feature to core. We really don't want to upset developers by having their hard work completely written off because the feature appears in core, we'd much rather recognise your hard work through contribution to core.

### Ghost (data) API

Principles:

- Data is either core data in the managed Ghost schema, or app data which is kept separately
- Apps can perform CRUD operations on Ghost data through the Ghost data API
- Apps can define new types of data, either related to existing tables, or stand alone - this is stored separately to core data tables
- Apps can define settings, these are stored in an app settings table, not the core settings table

#### App Settings

The separation between the core settings and app settings tables helps with the long-term management of data which comes from apps. In WP land, the options table is a mish-mash of rows some from WP itself, others from plugins, others from themes. We want to make sure that app data is easy to identify and separate from Ghost data.

Apps will be able to access the core settings table, but not add to it, or make changes to any setting marked 'core'. Those settings are for the core only. Any other setting may be modified but not deleted.

#### Custom data

As it stands, apps can require Knex and access the database directly. This works, but is laborious, and not the "one clear way to do things" approach we want app authors using.

tbc...