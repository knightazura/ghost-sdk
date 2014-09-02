The Roadmap aims to set out when certain features will appear. It reduces in clarity the further we go into the future, and is constantly being added to as we move forward.

If you're just looking to find out whether a feature is likely to end up in core or not, then take a look at the [planned features page](https://github.com/TryGhost/Ghost/wiki/Planned-Features). It's just a list, but we're adding more detail to it as we go.

## The Public Roadmap

The wiki Roadmap has been replaced with a [public trello board](https://trello.com/b/EceUgtCL/ghost-roadmap), to make it easier for everyone to keep track of ongoing work. If you would like to receive regular updates on our progress, you can subscribe to the [Dev Blog](http://dev.ghost.org) which is updated weekly after the public developer meeting.

[![](https://trello.com/b/EceUgtCL.png)](https://trello.com/b/EceUgtCL/ghost-roadmap)

For information on how the new roadmap works, see [visit trello](https://trello.com/c/0e0L0alW/65-how-does-this-roadmap-work-click-here-to-find-out).

## GitHub Backlogs

We now have just two Milestones on GitHub: 
- [0.5x Backlog](https://github.com/TryGhost/Ghost/issues?milestone=21) - contains issues which are ready to be worked on
- [Future Backlog](https://github.com/TryGhost/Ghost/issues?milestone=6) - contains issues which aren't ready to be worked on yet

The idea is that any issue in the 0.5.x backlog can be picked up and worked on. If the PR gets merged, the code goes out in the next release. We ask developers to use the [roadmap](https://trello.com/b/EceUgtCL/ghost-roadmap) as a guide to which features are most important for the next release, but this only covers features, not technical improvements or bug fixes.

## Past Milestones

#### Version 0.5 (11th August)

Release the API, Ember and Multi-User projects as Ghost 0.5

See [0.5.0](https://github.com/TryGhost/Ghost/commits/0.5.0)

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

## Past Projects:

## API

### In master Q2 2014

See the [Epic](https://github.com/TryGhost/Ghost/issues/2124) for an overview of the project, what was required and why. Additionally, see the [issue backlog](https://github.com/TryGhost/Ghost/issues?labels=&milestone=19&page=1&state=open) to pick up issues and monitor progress.

#### Goals:

* To standardise the Ghost data API by introducing a standard format which closely matches JSON-API
* To introduce new API endpoints needed for Apps, Themes and other core parts of Ghost.
* To introduce permissions / access control across the entire API
* To produce structure documentation of each endpoint, the expected response and any errors that may result

## Ember

The Ghost Admin will be rewritten in Ember.js as a full client side SPA, consuming the Ghost data API. This is a dependency for all features which depend on UI changes. This project was started several weeks ago, but has been put on hold so that everyone can focus on the refactoring work to the API which is a dependency if the Ember admin is ever going to work. We should be back to this project before the end of April.

See the [Epic](https://github.com/TryGhost/Ghost/issues/2271) for an overview of the project, what is required and why. Additionally, see the [issue backlog](https://github.com/TryGhost/Ghost/issues?milestone=17&state=open) to pick up issues and monitor progress.

#### Goals

* To rebuild the entire Ghost admin in Ember.js
* To resolve as many UI bugs/issues as possible
* To create a framework for rapid development of user interfaces in Ghost
* To lay the groundwork to deliver significant improvements for mobile
* ?To introduce a more holistic solution for managing keyboard shortcuts?

## Multi-user

Ghost will get the option to add multiple users, with differing roles and permissions. 

#### Goals
* To make it possible to have a multi-user blog
* To ensure that the admin UI is safe from XSS and other security issues
* To improve the first run/install and introduction experience for users

---



#### History 

For more history, please see the [pre-release roadmap](https://github.com/TryGhost/Ghost/wiki/Pre-release-Roadmap)