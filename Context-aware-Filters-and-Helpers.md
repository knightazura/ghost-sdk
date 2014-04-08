**NOTE:** Everything you read in here is a lie. No really, this is merely a draft summary of some open discussions in [#2249](https://github.com/TryGhost/Ghost/issues/2249), [#2567](https://github.com/TryGhost/Ghost/issues/2567) and [#2113](https://github.com/TryGhost/Ghost/issues/2113) do not rely on it.

## What does context awareness mean?

[Helpers](http://docs.ghost.org/themes/#helpers) in themes are applied and sometimes only available in certain contexts. The `{{has}}` helper currently only works in the context of a single post and lets the theme developer ask for a set of tags. Context-aware helpers allow the theme developer to ask for the context in which the current template is being rendered in.

Example: `post.hbs` and `index.hbs` can use a `_single.hbs` partial to render each individual post. Inside the partial it might be necessary to change the output depending on whether the partial is rendered inside `index.hbs` or `post.hbs`. 

## Context in helpers

The `{{#is}}` block helper provides a means to ask for the current context. 
 
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
    names: ['rss', 'paged'] // Context names
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

## Alternative Context Table

| name | url (default) | single | paged | template | body classes (current) | body classes (proposed) [WIP]| context | data |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| index (home) | / | F | F | index | home-template | _home-template_ | [index, home] | [{posts}], {pagination} |
| index paged| /page/2 | F | T | index | archive-template  | _paged_ | [index, home, paged] | [{posts}], {pagination} |
| single post | /my-post | T | F | post | post-template, tag-* | _post-template, tag-*_ | [post] | {post}
| single page | /my-page | T | F | page-{{slug}} or page or post | post-template, page, tag-* | _page-template, tag-*_ | [post, page] | {post}
| tag | /tag/my-tag/ | F | F | tag or index | tag-template, tag-* | _tag-template, tag-*_ | [tag] | [{posts}], {pagination}, {tag} |
| tag paged| /tag/my-tag/page/2/ | F | T | tag.hbs or index.hbs | archive-template, tag-template, tag-* | _tag-template, tag-*, paged_ | [tag, page] | [{posts}], {pagination}, {tag} |
| rss | /rss/ | F | F | n/a | n/a | n/a | | rss feed XML
| rss paged| /rss/2/ | F | T | n/a | n/a | n/a | | rss feed XML
| **coming in 0.6** | (maybe) | - | - | - | - | - | - |
| user | /user/my-user/ | F | F | user.hbs or index.hbs | n/a | _user-template, user-*_ | [{posts}], {pagination}, {user} |
| user paged| /user/my-user/page/2 | F | T | user.hbs or index.hbs | n/a | _user-template, user-*, paged_ | [{posts}], {pagination}, {user} |
| **coming in ??** | (maybe) | - | - | - | - | - | - |
| users | /users/ | F | F | users | n/a | | [{users}], {pagination} |
| users paged| /users/page/2/ | F | T | users | n/a | | [{users}], {pagination} |
| tags | /tags/ | F | F | tags | n/a | | | [{tags}], {pagination} |
| tags | /tags/page/2 | F | F | tags | n/a | | | [{tags}], {pagination} |
| archive | /archive/ | F | F | archive or index | n/a | | | [{posts}], {pagination} |
| archive paged| /archive/page/2/ | F | F | archive or index | n/a | | | [{posts}], {pagination} |

? - The concept of 'single' vs 'list' breaks down for tag pages as they represent a single tag, but a list of posts... or are 