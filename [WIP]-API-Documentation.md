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
Possible values are `draft` and `published`. `status` has influence on who can see your post and if it is shown on the frontpage of your blog.
- **markdown: string**<br/>
Content of your post encoded in markdown.
- **image: string**<br/>
Not used yet.
- **featured: boolean**<br/>
Indicate a featured post.
- **page: boolean**<br/>
Indicate if the post is a page.
- **language: string**<br/>
remark about language format, not used yet, defaults to
- **meta_title: string**<br/>
Not used yet.
- **meta_description: string**<br/>
Not used yet.
- **author_id: integer**<br/>
- **created_at: string**<br/>
remark about date/time
- **created_by: integer**, user - includeable<br/>
includeable when implemented
- **updated_at: string**<br/>
remark about date/time format
- **updated_by: integer**, user - includeable<br/>
includeable when implemented
- **published_at: string**<br/>
remark about date/time
- **published_by: integer**, user - includeable<br/>
includeable when implemented
- **author: object**, user<br/>
- **tags: array of objects**, tags<br/>

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
            image: null,
            featured: false,
            page: false,
            language: "en_US",
            meta_title: null,
            meta_description: null,
            author_id: 1,
            created_at: "2014-04-15T12:36:28.353Z",
            created_by: 1,
            updated_at: "2014-04-15T12:36:28.353Z",
            updated_by: 1,
            published_at: "2014-04-15T12:36:28.363Z",
            published_by: 1,
            author: { ... },
            tags: [{ ... }]
        }
    ]
}
```

## Retrieve an existing post

### Arguments
- **id: required**<br/>
ID of the post you would like to retrieve.
- **status: optional**<br/>
Possible values are `draft`, `published` and `all`.
- **staticPages: optional**<br/>
Include posts where the `page` attribute is `true`. Possible values are `true`, `false` and `all`.

### Permissions

 Admin         | Editor         | Author          | NoAuth 
---------------|----------------|-----------------|---------------
read all posts | read all posts | read posts with status `published` <br> or that were created by the user | read posts with status `published

### Usage
- `api.posts.read({id: id})`
- `GET /ghost/api/v0.1/posts/{id}/`

