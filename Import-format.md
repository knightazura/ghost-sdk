Ghost imports from existing blogs by having them export a JSON file and then reading that in.

## Existing Plugins to Automate this:

### Official
* WordPress users can use the [Ghost WordPress Plugin](http://wordpress.org/plugins/ghost/) to export their data.

### Non-official
* Jekyll users can use the [Jekyll to Ghost Plugin](https://github.com/redwallhp/Jekyll-to-Ghost)
* Blogger users can try [blogger2ghost](https://github.com/bebraw/blogger2ghost). Also available as a [web service](http://blogger2ghost.com/).
* Open-source geeks may consider importing READMEs from all of their Github repositories as regular posts using [gh2ost](https://github.com/RReverser/gh2ost) tool.

## Importing the JSON
Once you've generated the JSON go to `/ghost/debug` on your blog to access the import form.

## Rolling your own.

If no export tools exist for your current blogging system you'll need to create one that generates a JSON file as described here. There is a full example at the end of this file. Please note that your final JSON file should have no comments in the final format. Those are only included here for readability and explanatory purposes.

### JSON file structure

First and foremost, your JSON file must contain valid JSON. You can test your file is valid using the [JSONLint](http://jsonlint.com/) online tool.

The file structure can optionally be wrapped in `{"db":[...contents here...]}` - both with and without are valid Ghost JSON files.

You must include a `meta` block and a `data` block.

All IDs inside the file are relative to the file only, so if you have a `post` with `id: 1` and a `posts_tags` object which references `post_id: 1`, then those two things will be linked, but they do not relate to the `post` with `id: 1` in your database. The only exception is any reference in foreign key fields to a `user` with `id: 1`, i.e. `created_by: 1` as the user with `id: 1` in the import file is assumed to mean the user in the database with the `owner` role.

#### The meta block

`"meta":{"exported_on":1408552443891,"version":"003"}`

The `meta` block expects two keys, `exported_on` and `version`. `exported_on` should be an epoch timestamp in milliseconds, version should be the data version the import is valid for. Currently Ghost is on data version 003, see [version info](https://github.com/TryGhost/Ghost/wiki/Version-Info) for more details.

#### The data block

`"data": { "posts": [{...}, ...], "tags": [], "posts_tags": [], "users": [], "roles_users": []}`

The data block contains all of the posts, tags, and users that you want to import into your blog, as well as relationships between posts and tags and users and roles. Each item that you include should be an array of objects.


```
{
    "meta":{
        // epoch time in milliseconds
        "exported_on":  1388805572000,
        // Data version, current is 003
        "version":      "003"

    },
    "data":{
        "posts": [
            {
                "id":5,
                "title":        "my blog post title",
                "slug":         "my-blog-post-title",
                "markdown":     "the *markdown* formatted post body",
                "html":         "the <i>html</i> formatted post body",
                "image":        null,
                "featured":     0, // boolean indicating featured status
                "page":         0, // boolean indicating if this is a page or post
                "status":       "published", // or draft
                "language":     "en_US",
                "meta_title":   null,
                "meta_description":null,
                "author_id":    1, // the first user created has an id of 1
                "created_at":   1283780649000, // epoch time in millis
                "created_by":   1, // the first user created has an id of 1
                "updated_at":   1286958624000, // epoch time in millis
                "updated_by":   1, // the first user created has an id of 1
                "published_at": 1283780649000, // epoch time in millis
                "published_by": 1 // the first user created has an id of 1
            }
        ],
        "tags": [
            {
                "id":           3,
                "name":         "Colorado Ho!",
                "slug":         "colorado-ho",
                "description":  ""
            },
            {
                "id":           4,
                "name":         "blue",
                "slug":         "blue",
                "description":  ""
            }
        ],
        "posts_tags": [
            {"tag_id":3, "post_id":5},
            {"tag_id":3, "post_id":2},
            {"tag_id":4, "post_id":24}
        ],
        "users": [
            {
                "id":           2,
                "name":         "user's name",
                "slug":         "users-name",
                "email":        "user@example.com",
                "image":        null,
                "cover":        null,
                "bio":          null,
                "website":      null,
                "location":     null,
                "accessibility": null,
                "status":       "active",
                "language":     "en_US",
                "meta_title":   null,
                "meta_description": null,
                "last_login":   null,
                "created_at":   1283780649000, // epoch time in millis
                "created_by":   1, // the first user created has an id of 1
                "updated_at":   1286958624000, // epoch time in millis
                "updated_by":   1 // the first user created has an id of 1
            }
        ]
    }
}
```