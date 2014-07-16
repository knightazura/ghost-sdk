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

**Special Rules:**

- Visibility of posts is determined based on status
- Ownership of posts is based on the author property, not created_by. The post's owner has all rights regardless of role.

API Method        | Admin | Editor | Author                                        | NoAuth
------------------|-------|--------|-----------------------------------------------|------------------------
browse            | y     | y      | y (status == published or author == self) | y (status == published)
read              | y     | y      | y (status == published or author == self) | y (status == published)
edit              | y     | y      | y (author == self) | 
add               | y     | y      | y                                             | 
destroy           | y     | y      | y (author == self)                                                            

### Users

* The action a user can perform is determined by their role, and the role of the user on which they are acting
* The user with the owner role cannot be deleted

API Method | Admin | Editor | Author           | NoAuth
-----------|-------|--------|------------------|------------------------
browse     | y     | y      | y 
read       | y     | y      | y      | y (email removed)
edit       | y     | y  (user == self or user == author)      | y (user == self) | 
add        | y     | y (user == author)      |                  | 
delete     | y (user != owner) | y (user == author)

### Roles

API Method | Admin | Editor | Author           | NoAuth
-----------|-------|--------|------------------|------------------------
browse     | y     | ?      | ?

### Roles Users

i.e. adding a user with a given role / assign a role

API Method | Admin | Editor | Author           | NoAuth
-----------|-------|--------|------------------|------------------------
add admin  | y     |        | 
add editor | y     |        | 
add author | y     |   y    | 


API Method | Admin | Editor | Author           | NoAuth
-----------|-------|--------|------------------|------------------------
assign     | y     |   y (role = author)     | 

### Tags

API Method  | Admin | Editor | Author           | NoAuth
------------|-------|--------|------------------|------------------------
browse      | y     | y      | y                | y
read        | y     | y      | y                | y
edit        | y     | y      |  | 
add         | y     | y      |  y               | 
delete      | y     | y      |                  | 


### Slugs

API Method            | Admin | Editor | Author | NoAuth
----------------------|-------|--------|--------|--------
generate              | y     | y      | y        

### DB

API Method            | Admin | Editor | Author | NoAuth
----------------------|-------|--------|--------|--------
exportContent         | y     |        |        |
importContent         | y     |        |        |
deleteAllContent      | y     |        |        |

### Notifications

API Method  | Admin | Editor | Author           | NoAuth
------------|-------|--------|------------------|------------------------
browse      | y     |        |                  | 
add         | y     |        |                  | 
delete      | y     |        |                  | 

### Themes

API Method  | Admin | Editor | Author           | NoAuth
------------|-------|--------|------------------|----------------

### Apps

API Method  | Admin | Editor | Author           | NoAuth
------------|-------|--------|------------------|----------------

### Mail

API Method  | Admin | Editor | Author           | NoAuth
------------|-------|--------|------------------|----------------
send        | y     |        |                  | 
sendTest    | y     |        |                  | 

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