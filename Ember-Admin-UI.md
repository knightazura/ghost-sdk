This page is intended as a starting point for anyone getting involved in the Ember admin UI. It covers important details about how the Ember version works.

Currently, the Ember admin UI is being built on the `ember` branch as a whole-sale rewrite of the old admin UI. As we move towards merging this, this document should evolve from covering the quirks of the rewrite to informing developers about how the Ember admin UI is structured and why.

For an understanding of what the project involves, have a read of the [epic overview issue](https://github.com/TryGhost/Ghost/issues/2271) which will be updated with more info and progress as the project goes on.

### The ember admin

**NOTE:** The ember version of the admin lives at `/ghost/ember/`. 

This exists alongside the old admin UI, so don't be fooled by going to `/ghost/` and thinking it all looks done - that is the old admin!

We are keeping both versions in the master branch for now because we believed that the ember rewrite would encourage new contributors who would therefore benefit from having the old version on hand to compare and contrast when rebuilding components.

### The API

The API that currently exists for the old admin UI is incomplete. Several routes depended on oldschool server-side interactions - things like uploading and password resetting - because the old admin UI was not a single page app. The new Ember admin UI should be a SPA and therefore, it is fully intended that these routes will be moved onto the API. The API is being rewritten in master to closely match the [JSON-API](http://jsonapi.org/) standard. Therefore the ember Admin UI is being built against a mock API so that the API redevelopment doesn't hold up the ember branch.

As we build out the new components it is also necessary to mock out bits of the API - don't worry about getting it 100% right / meeting the JSON API standards, that will be done by someone else - just make it 'appear' to work :)

### About the models 

TBD
