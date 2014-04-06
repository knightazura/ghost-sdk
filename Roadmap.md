The Roadmap aims to set out when certain features will appear. It reduces in clarity the further we go into the future, and is constantly being added to as we move forward.

If you're just looking to find out whether a feature is likely to end up in core or not, then take a look at the [planned features page](https://github.com/TryGhost/Ghost/wiki/Planned-Features). It's just a list, but we're adding more detail to it as we go.

----

## Milestone 5 - Version 0.5.0 - Apps & Import

### Q2 2014

This is the current Milestone

Focuses on the app boilerplates, API, filters, importers, permissions, security and other app related things, to bring the first iteration of Ghost Apps to the public.

Open issues: [0.5](https://github.com/TryGhost/Ghost/issues?direction=desc&milestone=12&page=1&sort=updated&state=open)

Delivering the app platform for Ghost is a truly enormous project. To get a full grasp of what this entails, it is recommended that you read [Imagining-the-Ghost-Developer-Tools](https://github.com/TryGhost/Ghost/wiki/Imagining-the-Ghost-Developer-Kit). The roadmap here documents which aspects of the Ghost Developer Tools (GDT) we intend to deliver in 0.5, along with other areas of work that are required in order to deliver this first iteration of Apps.

There are 4 main areas of work that will take place in 0.5, known as [Apps](#apps), [Importer](#importer), [Themes](#themes) and [Other](#other). Each area and its individual goals are described below.

### Apps

Issue label: [apps](https://github.com/TryGhost/Ghost/issues?direction=desc&labels=apps&milestone=12&page=1&sort=updated&state=open)

By far the largest area of work, Apps encompasses work across both the [Ghost](https://github.com/TryGhost/Ghost) and [Ghost-App](https://github.com/TryGhost/Ghost-App) repositories. Work on this area is tracked through an [epic issue](https://github.com/TryGhost/Ghost/issues/1474) in the [Ghost](https://github.com/TryGhost/Ghost) repository. Watching this issue should allow any one interested to keep up-to-date on the progress of Ghost apps.

**Goal**: In Ghost version 0.5, it is expected that developers would be able to create simple apps for Ghost that achieve the most obvious additions, like comments, analytics custom helpers, and media handling improvements. App developers should *not* expect to have full access to all tools documented in the GDT in 0.5. Further updates will ship more advanced features.

**Tasks**:

* [ ] Settle on the App boilerplace, decide on v1.0 of the [Ghost-App](http://github.com/TryGhost/Ghost-App) module, and publish it to npm.
* [~] Add `package.json` support for apps, enabling developers to define key data about apps, and also define their own dependencies.
* [ ] Roll out ACL across the Ghost admin, ensuring all objects and routes are correctly permissioned.
* [ ] Introduce App permissions system to ensure that apps can only do the things for which they have permission.
* [ ] Create the App UIs for installation, activation and management.
* [ ] Update the schema to include tables for App settings, and create a way for Apps to define, access and provide UIs their own settings.
* [ ] Develop the App install process, which presents users with permissions, manages dependencies, etc etc.
* [ ] Create an intial set of filters which provides for overriding Ghost's behaviour via the Filter API.
* [ ] Ensure that error handling for Apps is top-notch, and introduce features for debugging.
* [ ] Finish up work to make the internal JSON data API consistent, and label it v1.0.
* [ ] Use the App proxy to provide access to an v1.0 of the Data API, Theme API and Filters API.

**If we have time**:

* Start work on the following parts of the GDT:
    * [ ] Routes API
    * [ ] Files API
    * [ ] Accounts API
    * [ ] The various toolsets
* [ ] Begin work on the dashboard, which is being planned separately from 0.5. See [note on the dashboard](#note-on-the-dashboard)


### Importer

Issue label: [importer](https://github.com/TryGhost/Ghost/issues?direction=desc&labels=importer&milestone=12&page=1&sort=updated&state=open)


**Goal**: In Ghost version 0.5, it should be possible to easily import a blog from a WXR or RSS file, by installing and using the official [Ghost Importer](https://github.com/TryGhost/Ghost-Importer) App. This App should serve as an example app, and also be easily extended to support more import formats.

**Tasks**:

* [ ] Develop a sexy new UI for the import tool, and move it to a new home.
* [ ] Make it possible for Apps to hook into and extend the import UI.
* [ ] Add support for more permalink structures, configured by the importer if possible.
* [ ] Build the Importer App, with initial support for WXR and RSS imports.
* [ ] Turn importing from a one-step do-or-die operation, into a several step process with opportunities to fix or discard invalid data.


### Themes

Issue label: [themes](https://github.com/TryGhost/Ghost/issues?direction=desc&labels=themes&milestone=12&page=1&sort=updated&state=open)


**Goal**: Every version of Ghost should deliver new features for themes, improving the overall blogging experience and providing new opportunities for theme developers to create fantastic themes.

**Tasks**:

* [ ] Create a set of placeholder style helpers which work together with filters for Apps, such as `{{comments}}` or `{{social}}`.
* [~] Improve error handling and debugging for themes.

### Other

**Goal**: Ghost 0.5 should significantly improve the ease of creating and customising a blog.

**Tasks**:

* [ ] Develop a brand new installation screen to be used instead of signup at first run.
* [ ] Introduce upgrade tools to bring us one step closer to 1-click upgrades.
* [ ] Add a timezone setting, which is used to display dates relative to the admin-user across the admin and theme.

#### Note on the dashboard

It was originally hoped / planned that the first version of the dashboard would be developed during 0.5, although it would be disabled by default until 0.6. However, at the moment, there are very few frontend developers involved with the Ghost project, and it doesn't seem realistic to include it.

Instead, the idea is to plan the work for the dashboard during 0.5, and see if we can put together a team of people to work on it as a sideproject during 0.5 and 0.6. For more information see [where is the dashboard?](https://github.com/TryGhost/Ghost/wiki/Planned-Features#wiki-where-is-the-dashboard)

----------
## Milestone 6 - Version 0.6.0 - Multi-user and Localisation

### Late Q2 / Early Q3 2014

Focuses firstly on adding multi-user functionality, so that you can run a multi-author blog, along with addressing the security concerns this introduces. Secondly, on providing the tools for l10n & i18n - making it possible for you to use Ghost in your language, and to publish blogs in any language. 

Open issues: [0.6](https://github.com/TryGhost/Ghost/issues?milestone=4&page=1&state=open)

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

----------
## Milestone 7 - Version 0.7.0 - Editor & Mobile

### Q3 2014

Rough Plan: - focus on overhauling and rebuilding the editor, bringing full mobile/multi-device support, markdown & media improvements etc

Open issues: [0.7](https://github.com/TryGhost/Ghost/issues?milestone=13&page=1&state=open)

----------
## Milestone 8 - Version 0.8.0 - Magazine Features

### Late Q3 / Early Q4 2014 

Rough Plan: focus on advanced publishing workflows, catering for bigger, more complex teams and also on more advanced theme features aimed at building magazine style blogs. 

Open issues: [0.8](https://github.com/TryGhost/Ghost/issues?milestone=14&page=1&state=open)

----------
## Milestone 9 - Version 0.9.0 - Cleanup 

### Q4 2014

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