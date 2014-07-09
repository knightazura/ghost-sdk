## Roles

| Name    | Description |
|:--------|:------------|
| Owner   | Automatically has all permissions. There can only ever be one owner, the owner cannot be deleted |
| Admin   | Has all permissions, except being able to transfer ownership of the blog |
| Editor  | Has permissions to manage their posts, and the posts of authors. Also has permissions to add and edit author users. |
| Author  | Has permissions to create and edit their own posts, and their own user details |
| No-Auth | User who is not authenticated - i.e. a reader on the blog


## Permissions

| Name       | Object Type | Action Type | API Endpoint   | 
|:-----------|:------------|:------------|:---------------|
| Edit posts | post        | edit        | PUT /posts/:id | 



## Role Permissions

### Posts
JSON API                 | Admin | Editor | Author                                        | NoAuth
-------------------------|-------|--------|-----------------------------------------------|------------------------
posts.browse             | y     | y      | y (status == published or created_by == self) | y (status == published)
posts.read               | y     | y      | y (status == published or created_by == self) | y (status == published)
posts.edit               | y     | y      | y (created_by == self) | 
posts.add                | y     | y      | y                                             | 
posts.destroy            | y     | y      | y (created_by == self)                        | 
posts.getSlug            | y     | y      | y                                             | 
