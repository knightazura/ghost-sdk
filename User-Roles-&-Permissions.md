## Roles

 Name    | Description |
:--------|:------------|
 Owner   | Automatically has all permissions. There can only ever be one owner, the owner cannot be deleted 
 Admin   | Has all permissions, except being able to transfer ownership of the blog |
 Editor  | Has permissions to manage their posts, and the posts of authors. Also has permissions to add and edit author users. |
 Author  | Has permissions to create and edit their own posts, and their own user details |
 No-Auth | User who is not authenticated - i.e. a reader on the blog


## Permissions

### Posts
API Method        | Admin | Editor | Author                                        | NoAuth
------------------|-------|--------|-----------------------------------------------|------------------------
browse            | y     | y      | y (status == published or created_by == self) | y (status == published)
read              | y     | y      | y (status == published or created_by == self) | y (status == published)
edit              | y     | y      | y (created_by == self) | 
add               | y     | y      | y                                             | 
destroy           | y     | y      | y (created_by == self)                        | 
getSlug           | y     | y      | y                                             | 
