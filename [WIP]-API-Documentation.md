Skip to:

* [Endpoints](#endpoints)
* [Post](#post)
* [Tag](#tag)
* [User](#user)

## Endpoints

### Posts

* `GET /ghost/api/v0.1/posts` - get all posts
    * Options:
        * page - pagination (default: 1)
        * limit - number of posts per page (default: 15)
        * status - status of the page (`all`, `published`, `draft`)
        * staticPages - include static pages (default: false)
* `POST /ghost/api/v0.1/posts` - add new post
* `GET /ghost/api/v0.1/posts/:id` - get post with id
* `GET /ghost/api/v0.1/posts/:slug` - get post with slug
* `PUT /ghost/api/v0.1/posts/:id` - update post with id
* `DELETE /ghost/api/v0.1/posts/:id` - delete post with id
* `GET /ghost/api/v0.1/posts/getSlug/:title` - get slug from title

### DB

* `GET /ghost/api/v0.1/db/` - export database
* `POST /ghost/api/v0.1/db/` - import database
* `DELETE /ghost/api/v0.1/db/` - delete content from database

### Notifications

* `DELETE /ghost/api/v0.1/notifications/:id` - delete notification
* `POST /ghost/api/v0.1/notifications/` - add new notification

### Settings

* `GET /ghost/api/v0.1/settings/` - get all settings
    * Options:
        * type (`blog`, `app`, `theme`) 
* `GET /ghost/api/v0.1/settings/:key/` - get setting with key
* `PUT /ghost/api/v0.1/settings/` - update settings

### Tags

* `GET /ghost/api/v0.1/tags/` - get all tags

### Users

* `GET /ghost/api/v0.1/users/` - get all users
* `GET /ghost/api/v0.1/users/:id/` - get user with id (`id=me` would be the current user)
* `PUT /ghost/api/v0.1/users/:id/` - update user with id



# Post

## The Post Object

### Attributes
- **id: integer**
- **uuid: string**<br/>
Unique identifier generated automatically as UUIDv4.
- **title: string**<br/>
Title of your blog post.
- **slug: string**<br/>
Automatically generated unique slug that is based on the title of your blog post (e.g.: 'Test Post' will become 'test-post').
- **status: string**<br/>
Possible values are `draft` and `published`. `status` has influence on who can see your post and if it is shown on the frontpage of your blog. Defaults to `draft`.
- **markdown: string**<br/>
Markdown of your post.
- **html: string**<br/>
HTML of your post generated from markdown.
- **image: string**<br/>
Not currently used.
- **featured: boolean**<br/>
Indicate a featured post. Defaults to `false`.
- **page: boolean**<br/>
Indicate if the post is a page. Defaults to `false`.
- **language: string**<br/>
Language of the post. Not currently used. Defaults to `en_US`. Language codes used as primary subtags are from ISO 639-1. Country codes used as secondary subtags are from ISO 3166. Primary and secondary tag are concatenated with an underscore.
- **meta_title: string**<br/>
Not currently used.
- **meta_description: string**<br/>
Not currently used.
- **author: integer**, user - includeable<br/>
Author of the post. By default the creator is used as initial author.
- **created_at: string**<br/>
ISO 8601 date and time when the post was created.
- **created_by: integer**, user - includeable<br/>
User who created the post.
- **updated_at: string**<br/>
ISO 8601 date and time when the post was last updated.
- **updated_by: integer**, user - includeable<br/>
User who last updated the post
- **published_at: string**<br/>
ISO 8601 date and time when the post was published.
- **published_by: integer**, user - includeable<br/>
User who published the post
- **tags: array of objects**, tags<br/>
Tags associated with the post.

### Example Post Object
```
{
    posts: [
        {
            status: "published",
            id: 1,
            uuid: "ec630e45-3342-4d7f-a24c-e448263c975b",
            title: "Welcome to Ghost",
            slug: "welcome-to-ghost",
            markdown: "",
            html: "",
            image: null,
            featured: false,
            page: false,
            language: "en_US",
            meta_title: null,
            meta_description: null,
            author: 1,
            created_at: "2014-04-15T12:36:28.353Z",
            created_by: 1,
            updated_at: "2014-04-15T12:36:28.353Z",
            updated_by: 1,
            published_at: "2014-04-15T12:36:28.363Z",
            published_by: 1,
            tags: [{ ... }]
        }
    ]
}
```

## Paginated List of Post Objects

### Attributes
- **posts: array**, post
- **meta: object**<br/>
Meta information for the result returned.
- **pagination: object**<br/>Pagination information.
- **page: integer**<br/>Number of the current page
- **limit: integer**<br/>Number of posts per page
- **pages: integer**<br/>Number of pages
- **total: integer**<br/>Number of total posts
- **next: integer**<br/>Number of next page, `null` if not available. 
- **prev: integer**<br/>Number of previous page, `null` if not available.

### Example Paginated List of Post Objects
```
{
    posts: [{...}],
    meta: {
        pagination: {
            page: 1,
            limit: 15,
            pages: 1,
            total: 1,
            next: null,
            prev: null
        }
    }
}
```

## Retrieve an Existing Post

Retrieves an existing post. In order to get a post the `id` or `slug` are needed to identify the post. The information returned when creating, updating or deleting is identical to retrieving a post.

### Usage

 API           | Example
---------------|----------------
Internal API   |`api.posts.read({id: id})`
HTTP Route     |`GET /ghost/api/v0.1/posts/{id}/`

### Arguments

- **id or slug: required**<br/>
ID of the post you would like to retrieve.

### Permissions

 Admin         | Editor         | Author          | NoAuth 
---------------|----------------|-----------------|---------------
read all posts | read all posts | read posts with status `published` <br> or that were created by the user | read posts with status `published



## Retrieve a Paginated List of Existing Posts

Retrieves a paginated list of post that exist in your database. By default only published posts are returned. It is possible to modify the filter using the `status` argument.

### Usage
- `api.posts.browse({status: 'draft'})`
- `GET /ghost/api/v0.1/posts/?status=draft`

### Arguments
- **status: optional**<br/>
Allowed values are `draft`, `published` and `all`.
- **staticPages: optional**<br/>
Include posts where the `page` attribute is `true`. Allowed values are `true`, `false` and `all`.


### Permissions

 Admin         | Editor         | Author          | NoAuth 
---------------|----------------|-----------------|---------------
read all posts | read all posts | read posts with status `published` <br> or that were created by the user | read posts with status `published`


## Create a new post

Create a new post. Tags that are sent with a new post are created if they don't exist and linked to the newly created post. The newly created post object is returned.

### Usage

 API           | Example
---------------|----------------
Internal API   |`api.posts.add(object, options)`
HTTP Route     |`GET /ghost/api/v0.1/posts/`

### Arguments
- **object: mandatory**<br/>
Data of the post that is going to be created. The object is expected to be a valid post object with mandatory and optional properties.

*Mandatory post properties:*

- title
- markdown
    
*Optional post properties:*

- slug
- status
- image
- featured
- page
- language
- meta_title
- meta_description
- author

- **options: optional**<br/>
TBD


### Permissions

 Admin         | Editor         | Author          | NoAuth 
---------------|----------------|-----------------|---------------
create post    | create post    | create post     | -

## Edit an existing post

Update a post that already exists. In order to update a post the `id` is needed to identify the post. The edited post object is returned.

### Usage
 API           | Example
---------------|----------------
Internal API   |`api.posts.edit(object, options)`
HTTP Route     |`PUT /ghost/api/v0.1/posts/<id>/`

### Arguments
- **object: mandatory**<br/>
A valid post object with properties that should be updated.

*Mandatory post properties:*

- id

*Updateable post properties:*

- slug
- title
- markdown
- status
- image
- featured
- page
- language
- meta_title
- meta_description
- author
- published_at

- **options: optional**<br/>
TBD

### Permissions

 Admin         | Editor         | Author          | NoAuth 
---------------|----------------|-----------------|---------------
edit all posts | edit all posts | edit all posts that were<br> create by the user | -

## Delete a post

Delete an existing post. In order to delete a post the `id` is needed to identify the post. The deleted post object is returned.

### Usage
 API           | Example
---------------|----------------
Internal API   |`api.posts.destroy(options)`
HTTP Route     |`DELETE /ghost/api/v0.1/posts/<id>/`

### Arguments
- **options: optional**<br/>
TBD


### Permissions

 Admin         | Editor         | Author          | NoAuth 
---------------|----------------|-----------------|---------------
delete all posts | delete all posts | delete all posts that were<br> create by the user | -
# Tag

## The Tag Object

### Attributes

- **id: increments**<br/>
- **uuid: string**<br/>
Unique identifier generated automatically as UUIDv4.
- **name: string**<br/>
Name of the tag.
- **slug: string**<br/>
Automatically generated unique slug that is based on the name of your tag (e.g.: 'Test Tag' will become 'test-tag').
- **description: string**<br/>
Not currently used.
- **parent_id: integer**<br/>
Not currently used.
- **meta_title: string**<br/>
Not currently used.
- **meta_description: string**<br/>
Not currently used.
- **created_at: dateTime**<br/>
Remark about date/time
- **created_by: integer**<br/>
Includeable when implemented
- **updated_at: dateTime**<br/>
Remark about last updated date/time.
- **updated_by: integer**<br/>
User id of last update author.

### Example Tag Object

```
{
      tags: [{
            "id": 1,
            "uuid": "c912cb47-fe10-4120-aca3-19feb1a931d6",
            "name": "Getting Started",
            "slug": "getting-started",
            "description": null,
            "parent_id": null,
            "meta_title": null,
            "meta_description": null,
            "created_at": "2014-03-12T17:04:00.819Z",
            "created_by": 1,
            "updated_at": "2014-03-12T17:04:00.819Z",
            "updated_by": 1
      }]
}
```

### Usage
- `api.tags.browse()`
- `GET /ghost/api/v0.1/tags/`

# User

## The User Object

### Attributes
- **id: integer**
- **uuid: string**  
Unique identifier generated automatically as UUIDv4.


### Example User Object
```
{
    users: [
        {
            
        }
    ]
}
```