**NOTE:** Everything you read in here is a lie. No really, this is merely a draft summary of some open discussions in [#2249](https://github.com/TryGhost/Ghost/issues/2249), [#2567](https://github.com/TryGhost/Ghost/issues/2567) and [#2113](https://github.com/TryGhost/Ghost/issues/2113) do not rely on it.

## What does context awareness mean?

[Helpers](http://docs.ghost.org/themes/#helpers) in themes are applied and sometimes only available in certain contexts. The `{{has}}` helper currently only works in the context of a single post and lets the theme developer ask for a set of tags. Context-aware helpers allow the theme developer to ask for the context in which the current template is being rendered in.

Example: `post.hbs` and `index.hbs` can use a `_single.hbs` partial to render each individual post. Inside the partial it might be necessary to change the output depending on whether the partial is rendered inside `index.hbs` or `post.hbs`. 

## Context in helpers

The `{{#is}}` block helper provides a means to ask for the current context. It can be used to render posts 
 
* `{{#is "home"}}` -> true if we’re on the homepage, false on any other page
* `{{#is "single"}}` -> true if we're on a post or static page
* `{{#is "tag"}}` -> true if we’re on a tag page

Lists: 

* `{{#is "home-list"}}` -> true if we’re on the normal post listing (`homepage` + `paged`)
* `{{#is "tag-list"}}` -> true if we’re on a tag page (`tag` + `paged`)

Special:

* `{{#is "paged"}}` -> true if we’re on page 2, 3, etc of the home or tag listings
* `{{#is "list"}}` -> true if we’re on any home, tag, or paginated listing page


## Context in filters

An app can use filters by providing a callback function. A filter can modify data that is passed to it. In addition to the data, filters also get a second parameter that provides contextual information. The `names` key contains the list of currently active contexts.

### Example 1: Change feed title on paged feed

```javascript
this.ghost.filters.register('rss.feed', function (data, context) {
    if (_.contains(context.name, 'paged')) {
        // Changes feed title based on context
        data.title = data.title + " archive";
    }

    return data;
});
```

```javascript
filters.doFilter('rss.feed', feed, {
    names: ['rss'] // Context name
    paged: true
});
```

### Example 2: Add `<audio>` player when rendering post on frontend

```javascript
this.ghost.filters.register('post.render', function (html, context) {
    if (_.contains(context.name, 'home-list')) {
        // Fetch app_fields for post.id
        audioFile = appFields.fetch(post.id, 'audioFile');
        html = "<audio>" + audioFile + "</audio>" + html;
    }

    return html;
});
```

```javascript
filters.doFilter('post.render', html, {
    names: ['home', 'home-list'],
    post: post
});
```

## Context Table

|           | / | /single-post | /page/2 | /tag/ghost | /tag/ghost/page/2 |
|-----------|:-:|:------------:|:-------:|:----------:|:-----------------:|
| home      | x |              |    x    |            |                   |
| single    |   |       x      |         |            |                   |
| tag       |   |              |         |      x     |         x         |
| paged     |   |              |    x    |            |         x         |
| list      |   |              |    x    |            |         x         |
| home-list | x |              |    x    |            |                   |
| tag-list  |   |              |         |      x     |         x         |