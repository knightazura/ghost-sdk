**NOTE:** Everything you read in here is a lie. No really, this is merely a draft summary of some open discussions in [#2249](https://github.com/TryGhost/Ghost/issues/2249), [#2567](https://github.com/TryGhost/Ghost/issues/2567) and [#2113](https://github.com/TryGhost/Ghost/issues/2113) do not rely on it.

## What does context awareness mean?

[Helpers](http://docs.ghost.org/themes/#helpers) in themes are applied and sometimes only available in certain contexts. The `{{has}}` helper currently only works in the context of a single post and lets the theme developer ask for a set of tags. Context-aware helpers allow the theme developer to ask for the context in which the current template is being rendered in.

Example: `post.hbs` and `index.hbs` can use a `_single.hbs` partial to render each individual post. Inside the partial it might be necessary to change the output depending on whether the partial is rendered inside `index.hbs` or `post.hbs`. 

## Context in helpers

The `{{#is}}` block helper provides a means to ask for the current context. 
 
* `{{#is "index"}}` -> true if we’re on the default post listing (`/`, `/page/2`, ...)
* `{{#is "post"}}` -> true if we're on a post or static page
* `{{#is "tag"}}` -> true if we’re on a tag page (including paged)

Special:

* `{{#is "paged"}}` -> true if we’re on page 2, 3, etc of the home, tag, user listings


## Context in filters

An app can use filters by providing a callback function. A filter can modify data that is passed to it. In addition to the data, filters also get a second parameter that provides contextual information. The `names` key contains the list of currently active contexts.

### Example 1: Change feed title on paged feed

```javascript
this.ghost.filters.register('rss.feed', function (data, context) {
    if (_.contains(context.names, 'paged')) {
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

Note: `post.render` doesn’t actually exist.

```javascript
this.ghost.filters.register('post.render', function (html, context) {
    if (_.contains(context.names, 'index')) {
        // Fetch app_fields for post.id
        audioFile = appFields.fetch(post.id, 'audioFile');
        html = "<audio>" + audioFile + "</audio>" + html;
    }

    return html;
});
```

```javascript
filters.doFilter('post.render', html, {
    names: ['index'],
    post: post
});
```

## Context Table

| name | url (default)| template | body classes (old) | body classes (proper)| context | data |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| index (home) | / | home.hbs or index.hbs | home-template | _home-template_ | [index, home] | [{posts}], {pagination} | [{posts}], {pagination}
| index paged| /page/2 | index.hbs | archive-template  | _paged_ | [index, paged] | [{posts}], {pagination} 
| post | /my-post | post.hbs | post-template, tag-* | _post-template, tag-*_ | [post] | {post} | {post}
| page | /my-page | page-{{slug}}.hbs or page.hbs or post.hbs | post-template, page, tag-*, (page-template-{{slug}}) | _page-template, tag-*, (page-{{slug}})_ | [page] | {post} | {post}
| tag | /tag/my-tag/ | tag.hbs or index.hbs | tag-template, tag-* | _tag-template, tag-*_ | [tag] | [{posts}], {pagination}, {tag} |
| tag paged| /tag/my-tag/page/2/ | tag-{{slug}}, tag.hbs or index.hbs | archive-template, tag-template, tag-* | _tag-template, tag-*, paged_ | [tag, paged] | [{posts}], {pagination}, {tag} |
| rss | /rss/ | n/a | n/a | n/a | [rss] | rss feed XML
| rss paged| /rss/2/ | n/a | n/a | n/a | [rss, paged] | rss feed XML
| author| /author/my-user/ | author.hbs or index.hbs | n/a | _author-template, author-*_ | [author] | [{posts}], {pagination}, {author} |
| author paged | /author/my-user/page/2 | author.hbs or index.hbs | n/a | _author-template, author-*, paged_ | [author, paged] | [{posts}], {pagination}, {author} |
| **coming in ??** | (maybe) | - | - | - | - | - | - |
| users | /users/ | users.hbs | n/a | | [users] | [{users}], {pagination} |
| users paged| /users/page/2/ | users.hbs | n/a | | [users, paged] | [{users}], {pagination} |
| tags | /tags/ | tags.hbs | n/a | | [tags] | [{tags}], {pagination} |
| tags | /tags/page/2 | tags.hbs | n/a | | [tags, paged] | [{tags}], {pagination} |
| archive | /archive/ | archive.hbs or index.hbs | n/a | | [archive] | [{posts}], {pagination} |
| archive paged| /archive/page/2/ | archive.hbs or index.hbs | n/a | | [archive, paged] | [{posts}], {pagination} |
