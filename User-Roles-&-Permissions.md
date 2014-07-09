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

### Users
JSON API  | Admin | Editor | Author           | NoAuth
----------|-------|--------|------------------|------------------------
browse    | y     | y      | 
read      | y     | y      | y      | y (email removed)
edit      | y     | y  (user == self or user == author)      | y (user == self) | 
add       | y     | y (user == author)      |                  | 
delete    | y (user != owner) | y (user == author)

### DB

API Method               | Admin | Editor | Author | NoAuth
-------------------------|-------|--------|--------|--------
db.exportContent         | y     |        |        |
db.importContent         | y     |        |        |
db.deleteAllContent      | y     |        |        |

### Notifications

### Settings

API Method               | Admin | Editor | Author           | NoAuth
-------------------------|-------|--------|------------------|------------------------
settings.browse          |       |        |                  | 
- core                   |       |        |                  | 
- blog                   | y     | y      | y                | y
- app                    | y     | y      | y                | 
- theme                  | y     | y      | y                | 
settings.read            |       |        |                  | 
- core                   |       |        |                  | 
- blog                   | y     | y      | y                | y
- app                    | y     | y      | y                | 
- theme                  | y     | y      | y                | 
settings.edit            |       |        |                  | 
- core                   |       |        |                  | 
- blog                   | y     |        |                  |  
- app                    | y     |        |                  | 
- theme                  | y     |        |                  | 