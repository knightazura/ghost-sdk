Ghost tags are intended to be a super-feature - a powerhouse of customisability for your blog. Tags are a single flexible and powerful concept of a taxonomy which should provide all the features a blog could need to categorise and list posts in interesting ways. 

Although they've started from humble beginnings, all that is about to change with the addition of tag management and the ability to query the API directly from your theme. This document outlines the vision for tags, starting with where we are and what we're building right now and covering the full suite of advanced we hope to deliver.

## The current state of tagging

Right now, all we have is simple component for adding tags to a post, and a basic helper to output them for each post. 

### Adding tags

The tag editor lives at the bottom of the post editor. This component features an input where you can type a tag. Typing a comma, enter or tab will finish the current tag and let you enter another. A popup appears over the component to suggest tags similar to what you're typing.

![](http://puu.sh/cXvID.png)

This tag input has suffered from quite a few bugs, both in terms of the UI display, and the input of tags. Tags are quite complex as they can contain any character apart from a comma. This includes containing special characters and things that might look like HTML. Unfortunately we haven't always done a good job of deduplicating tags based on whitespace and case. This has been the cause of a number of issues with duplicate tags which cannot be cleaned up.

Further still, the UI is quite subtle, and some users miss it entirely! I think we'll see this component get redesigned and rebuilt to be more robust in the not-too-distant future.

### Theming

For Ghost themes, the `{{tags}}` helper will output the tags related to a post in a comma separated list. It can be customised slightly, or theme developers can use the `{{#foreach}}` helper to loop through and output more complex tag lists manually.

![](http://puu.sh/cYOf4.png)

The `{{tags}}` helper only works for outputting the tags related to a post, there is currently no way to output a full list of the tags for a blog or to create a tag cloud. Additionally, Ghost does not pay attention to what order the tags are output at the moment - it changes dependent on the database default. These limitations of the `{{tags}}` helper causes some frustration.

One additional feature that is available in themes, is the `{{#has}}` helper. This allows for checking whether a post has a particular tag or set of tags associated with it or not, for example something like `{{#has tag="photo"}}` can be used to output a different class or other HTML for photo posts. This provides the ability to style posts differently in a way similar to if we had post types.


## Adding tag management

We need to add tools for managing & using the tags associated across a blog if they are going to be truly useful. The original end goal for the tag management interface looked like this (note this screenshot shows a modal instead of the new settings menu component):

![](https://cloud.githubusercontent.com/assets/120485/3268400/55870c3a-f2dc-11e3-8b07-128091ff85fe.png)

Visible in this design is a number of advanced features like search, tag visibility and tag hierarchy. These features are described later in this document. For now we're going to focus on the first iteration.

### Basic Tag Management

We're working on a first version of tag management that we can ship quickly. The work is tracked and planned in the [epic issue #4248](https://github.com/TryGhost/Ghost/issues/4248). This first version will feature a simple list, which shows all of the tags in the database, along ith it's URL and a count of how many posts the tag is associated with.

![screenshot of simple tag list](http://puu.sh/cZyOy.png)

Clicking on any tag will display a settings menu similar to the one on the editor, which will provide for editing the tag's name, slug, description, cover image and meta data. It will also be possible to delete the tag.

![screenshot of edit screen](http://puu.sh/cZAA0.png)

Clicking new tag opens up an interface with blank fields so that a new tag can be added. 

The biggest remaining complexity in this, is updating the API so that when fetching tags it is possible to find out how many posts it is associated with.

This is the point at which we will remove the config flag and make this screen available to all users.

## Advanced features

With basic tag management out in the wild, here are the details of the advanced features we plan to ship.

### The query helper 

The query helper is currently being discussed on [GitHub](https://github.com/TryGhost/Ghost/issues/4439). This will make it possible to query the API directly and fetch a list of all tags with any filtering or other options provided by the API. Something like `{{#fetch "tags" limit="all"}}`

As part of the tag management improvemens, we ought to consider whether the `{{tags}}` helper ought to be an alias for querying tags when used outside of the post scope.

Opening up the API in this way is likely to result in a number of requests for additional behaviour in the tag and posts API, the most obvious of which is tag order...

### Tag order

As mentioned earlier, we don't currently pay any attention to what order tags are output. There are a couple of 'orders' that I can imagine will be in high demand:

- output tags related to post in the order they appear in the editor. This is going to come with additional requirements like adding drag&drop reordering to tags in the editor, and needing a concept of order in the posts_tags table.
- output tags in alphabetical order
- output tags in order of popularity (number of posts the are associated with).


### Associated Posts

The new management UI will show a number for how many posts a particular tag is associated with. Ideally, it would be great to be able to click on this or otherwise interact with the tag to discover a list of which posts a tag is associated with and remove a tag from a particular post (or go to the editor to do this).

### Visibility

The concept of visibility in tags, is that it's desirable to be able to mark some tags as 'private' such that the tag is not listed out in the tag list for a post. Additionally private tags would not have an archive page or be returned from the API by default. 

The `{{#has}}` helper would still return true if a post has that tag associated with it. This would build on the ability to use tags to create post types or other taxonomies that create structure for a blog. 

### Hierarchy

This will likely be limited to 2-3 levels of parent, child and sub-child tags, but will provide the ability for creating structured taxonomies around which more complex navigation could be built into a blog.

Implementing this will require quite a bit of work on the API, and on figuring out use cases for themes so that it is possible to make best use of the feature.

### Canonical / Primary

The one thing that a single tag taxonomy doesn't provide is the ability to define one of the tags associated with a post as being the primary, or canonical tag for a post.

This means it's not possible to create post permalinks which contain a main category like `/:primary_tag/:slug/`. It is desirable that we make this possible at some point.


### URL settings

All tag archives are currently output at the url `/tag/:tag_slug/`. This doesn't suit all blogs, and we want to make it possible to translate or otherwise change the `/tag/` part (as well as the `/author/` part of author URLs).

### New UI 

Undoubtably at some point we'll want to completely rebuild the tag UI in the post editor, to make it more robust and flexible. This will be needed if we want to properly support tag ordering, primary tags, etc.

### Search

At some point we need to roll search across the whole API so that it's possible to locate post, tag and user objects using plain text search. We will then build search into the tag management UI etc.