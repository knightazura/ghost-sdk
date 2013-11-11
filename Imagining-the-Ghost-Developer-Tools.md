The Ghost Developer Tools (GDTs) are a set of APIs which allow dvelopers to build apps on top of the Ghost platform.

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


Essentially, the core should provide the tools for apps to use in creative ways. The tools provide power and flexibility to be used in ways we cannot imagine - pretty much anything should be possible. Any restrictions should exist only where it serves the GDT principles or protects the core of Ghost. 

### Apps should not

* Do anything illegal
* Compromise the security or integrity of a Ghost blog
* Compromise user data or privacy
* Do anything to damage the Ghost brand or trademark


### The fundamentals

The first principle of creating a Ghost app is creating consistency in the code and in the end user experience. To do this, all apps will start out with a set of meta data provided through a package.json file, including a name, description, keywords, an icon etc.

The Ghost admin panel will have an Apps screen displaying any install apps, much like you might see on a mobile OS. Each app will have a name and be represented by an icon. Clicking on an app will take you to a managment or settings page for that application. Every application will have its own screen, and this is the only place where an app will be able to provide settings.

Apps will be able to register other entities which may be managed elsewhere, such as widgets for the dashboard, accounts for 3rd parties, custom post data, embeddable content etc. With each type of thing having it's own consistent location in the UI.

A key example of how all this will work is dashboard widgets. A button on the dashboard will take you to a list of available widgets, whether they are part of core or provided by an app. A widget can be added to the dashboard, and then customised with its own set of settings. Widgets can be dragged around, resized and removed from the dashboard.

The GDTs will provide the tools for registering a widget and then defining its content, interactions, available sizes and settings in the most straightforward way possible whilst maintaining all the flexibility of effectively providing a mini-app all in itself.