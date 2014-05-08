The Roadmap aims to set out when certain features will appear. It reduces in clarity the further we go into the future, and is constantly being added to as we move forward.

If you're just looking to find out whether a feature is likely to end up in core or not, then take a look at the [planned features page](https://github.com/TryGhost/Ghost/wiki/Planned-Features). It's just a list, but we're adding more detail to it as we go.

**Update: 15th April 2014**

The roadmap has been changed to become project focused, rather than milestone focused to help the team deliver. Each project listed here in the Roadmap is listed in the order they will be done. Projects don't get a Ghost version in advance, but they do have an estimated delivery date. As we pick up each project, we'll assign a number of weeks / end date for the project - no project should last more than 4 weeks.

The first project, API, is a dependency for the Ember project, Apps project and Multi-user project, which is why it is the first priority. The Ember project is required to deliver any features which require amends or additions to the admin UI. The Multi-user project has been brought forward as it is a highly requested feature, and the majority of the work is done by the API & Ember changes.

---

## API

### Est. Q2 2014

**This is the currently active project, please help us by picking up an [API issue](https://github.com/TryGhost/Ghost/issues?labels=&milestone=19&page=1&state=open), Thanks!**

The API project is a dependency for the Ember, Multi-user and Apps projects. It involves changing the request and response formats of the internal data API to be clear and consistent, adding missing API endpoints, and implementing permissions across the API.

See the [Epic](https://github.com/TryGhost/Ghost/issues/2124) for an overview of the project, what is required and why. Additionally, see the [issue backlog](https://github.com/TryGhost/Ghost/issues?labels=&milestone=19&page=1&state=open) to pick up issues and monitor progress.

#### Goals:

* To standardise the Ghost data API by introducing a standard format which closely matches JSON-API
* To introduce new API endpoints needed for Apps, Themes and other core parts of Ghost.
* To introduce permissions / access control across the entire API
* To produce structure documentation of each endpoint, the expected response and any errors that may result

---

## Ember

### Est. Q2 2014

**This is the currently active project, please help us by picking up an [Ember issue](https://github.com/TryGhost/Ghost/issues?milestone=17&state=open), Thanks!**

The Ghost Admin will be rewritten in Ember.js as a full client side SPA, consuming the Ghost data API. This is a dependency for all features which depend on UI changes. This project was started several weeks ago, but has been put on hold so that everyone can focus on the refactoring work to the API which is a dependency if the Ember admin is ever going to work. We should be back to this project before the end of April.

If you are interested in helping out with the Ember work, please take a look at the [ember](https://github.com/TryGhost/Ghost/tree/ember) branch. 

The old admin is still located at `/ghost/` and the new Ember admin lives at `/ghost/ember/`

See the [Epic](https://github.com/TryGhost/Ghost/issues/2271) for an overview of the project, what is required and why. Additionally, see the [issue backlog](https://github.com/TryGhost/Ghost/issues?milestone=17&state=open) to pick up issues and monitor progress.

#### Goals

* To rebuild the entire Ghost admin in Ember.js
* To resolve as many UI bugs/issues as possible
* To create a framework for rapid development of user interfaces in Ghost
* To lay the groundwork to deliver significant improvements for mobile
* ?To introduce a more holistic solution for managing keyboard shortcuts?

---

## Multi-user

### Est. Q2 2014

Ghost will get the option to add multiple users, with differing roles and permissions. 

#### Goals
* To make it possible to have a multi-user blog
* To ensure that the admin UI is safe from XSS and other security issues
* To improve the first run/install and introducton experience for users

---

## Upgrades
### Est. Q3 2014

Introduce an internal tool for upgrading Ghost

----

## Apps Part 1
### Est. Q3 2014
Focuses on the app boilerplates, API, filters, importers, permissions, security and other app related things, to bring the first iteration of Ghost Apps to the public.



Open issues: [0.5](https://github.com/TryGhost/Ghost/issues?direction=desc&milestone=12&page=1&sort=updated&state=open)

Delivering the app platform for Ghost is a truly enormous project. To get a full grasp of what this entails, it is recommended that you read [Imagining-the-Ghost-Developer-Kit](https://github.com/TryGhost/Ghost/wiki/Imagining-the-Ghost-Developer-Kit). The roadmap here documents which aspects of the Ghost Developer Kit (GDK) we intend to deliver in 0.5, along with other areas of work that are required in order to deliver this first iteration of Apps.

Apps encompasses work across both the [Ghost](https://github.com/TryGhost/Ghost) and [Ghost-App](https://github.com/TryGhost/Ghost-App) repositories. Work on this area is tracked through an [epic issue](https://github.com/TryGhost/Ghost/issues/1474) in the [Ghost](https://github.com/TryGhost/Ghost) repository. Watching this issue should allow any one interested to keep up-to-date on the progress of Ghost apps.

#### Goals
* app developers willbe able to create simple apps for Ghost that achieve the most obvious additions, like comments, analytics custom helpers, and media handling improvements. 
* app developers should *not* expect to have full access to all tools documented in the GDK. Further updates will ship more advanced features.

#### Tasks

* [ ] Settle on the App boilerplace, decide on v1.0 of the [Ghost-App](http://github.com/TryGhost/Ghost-App) module, and publish it to npm.
* [~] Add `package.json` support for apps, enabling developers to define key data about apps, and also define their own dependencies.
* [ ] Introduce App permissions system to ensure that apps can only do the things for which they have permission.
* [ ] Create the App UIs for installation, activation and management.
* [ ] Update the schema to include tables for App settings, and create a way for Apps to define, access and provide UIs their own settings.
* [ ] Develop the App install process, which presents users with permissions, manages dependencies, etc etc.
* [ ] Create an intial set of filters which provides for overriding Ghost's behaviour via the Filter API.
* [ ] Ensure that error handling for Apps is top-notch, and introduce features for debugging.
* [ ] Use the App proxy to provide access to an v1.0 of the Data API, Theme API and Filters API.

**If we have time**:

* Start work on the following parts of the GDT:
    * [ ] Routes API
    * [ ] Files API
    * [ ] Accounts API
    * [ ] The various toolsets
* [ ] Begin work on the dashboard, which is being planned separately from 0.5. See [note on the dashboard](#note-on-the-dashboard)

---

## Importer Part 1

### Est. ?? 2014

Issue label: [importer](https://github.com/TryGhost/Ghost/issues?direction=desc&labels=importer&milestone=12&page=1&sort=updated&state=open)

#### Goals
* make it possible to easily import a blog from a WXR or RSS file, by installing and using the official [Ghost Importer](https://github.com/TryGhost/Ghost-Importer) App. This App should serve as an example app, and also be easily extended to support more import formats.

#### Tasks

* [ ] Develop a sexy new UI for the import tool, and move it to a new home.
* [ ] Make it possible for Apps to hook into and extend the import UI.
* [ ] Add support for more permalink structures, configured by the importer if possible.
* [ ] Build the Importer App, with initial support for WXR and RSS imports.
* [ ] Turn importing from a one-step do-or-die operation, into a several step process with opportunities to fix or discard invalid data.

---

## Localisation

### Est. ?? 2014

Focuses firstly on adding multi-user functionality, so that you can run a multi-author blog, along with addressing the security concerns this introduces. Secondly, on providing the tools for l10n & i18n - making it possible for you to use Ghost in your language, and to publish blogs in any language. 

---

## Dashboard

### Est. ?? 2014

For more information see [where is the dashboard?](https://github.com/TryGhost/Ghost/wiki/Planned-Features#wiki-where-is-the-dashboard)

---

## Milestone 7 - Version 0.7.0 - Editor

### Est. ?? 2014

Rough Plan: - focus on overhauling and rebuilding the editor, bringing full mobile/multi-device support, markdown & media improvements etc

Open issues: [0.7](https://github.com/TryGhost/Ghost/issues?milestone=13&page=1&state=open)

---
## Milestone 8 - Version 0.8.0 - Magazine Features

### Est. ?? 2014 

Rough Plan: focus on advanced publishing workflows, catering for bigger, more complex teams and also on more advanced theme features aimed at building magazine style blogs. 

Open issues: [0.8](https://github.com/TryGhost/Ghost/issues?milestone=14&page=1&state=open)

---
## Milestone 9 - Version 0.9.0 - Cleanup 

### Est. ?? 2014 

Rough Plan: focus on anything which is still missing and required for 1.0.0. This is currently an open ended opportunity to refactor, tidy up, finish off features, add finishing touches etc etc 

Open issues: [0.9](https://github.com/TryGhost/Ghost/issues?milestone=15&page=1&state=open)

## Future Releases

See [planned features](https://github.com/TryGhost/Ghost/wiki/Planned-Features) for an idea of what will be happening.

## Past Milestones

#### Version 0.4.2

Maintenance release with many new features

See [Milestone History](https://github.com/TryGhost/Ghost/wiki/Roadmap-History:-Milestone-4---Version-0.4.0#version-042---theme-updates--major-fixes) or the [release post](http://blog.ghost.org/ghost-0-4-2-maintenance-release/)

#### Version 0.4.1 (30th Jan)

Maintenance release, see [0.4.1](https://github.com/TryGhost/Ghost/commits/0.4.1)

#### Milestone 4 - Version 0.4.0 (13th Jan)

See [Milestone History](https://github.com/TryGhost/Ghost/wiki/Roadmap-History:-Milestone-4---Version-0.4.0) or the [Release Notes](https://github.com/TryGhost/Ghost/wiki/Release-Notes:-0.4.0)

#### Version 0.3.3 (18th of Oct)

Maintenance & security release, see [0.3.3](https://github.com/TryGhost/Ghost/commits/0.3.3)

#### Version 0.3.2 (12th Oct), followed by Public release (14th Oct)

Maintenance release, see [0.3.2](https://github.com/TryGhost/Ghost/commits/0.3.2)

#### Version 0.3.1 (27th Sep)

Maintenance release, see [0.3.1](https://github.com/TryGhost/Ghost/commits/0.3.1)

#### Milestone 3 - Version 0.3.0 - Kickstarter release

See [0.3.0](https://github.com/TryGhost/Ghost/commits/0.3.0)



#### History 

For more history, please see the [pre-release roadmap](https://github.com/TryGhost/Ghost/wiki/Pre-release-Roadmap)