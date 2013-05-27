(This is very much a work in progress)

**Global questions**: 
 * Should everything have a uuid?

## Posts

**Questions**: 
 * Should we have a secondary meta data table like WP or allow plugins to actually add columns to the table? 
 * How can we allow for custom fields?
 * Do we need a 'type' field?

**Permissions**: create, edit, delete, view and various state changing permissions i.e. can change state to.. approved, published, etc. 
Advanced workflows are not on the roadmap for some time, but we need to leave the doors open for implementing this.

- id - incrementing primary key
- title - String
- slug - String (url)
- content - Text
- content_html - Text
- featured - Boolean
- image - Currently we store reference to a single image on the post, but I think this needs to be moved 
- status - one of: 'draft', 'complete', 'approved', 'scheduled' or 'published'
- language String - not sure what the best format to use is, I was thinking en_GB/en_US?
- author_id - author could be different to creator, not sure if this matters
- created_at - timestamp
- created_by - timestamp
- updated_at - timestamp
- updated_by - timestamp
- published_at - timestamp
- published_by - timestamp

## Category / Tag

Categoristion which supports hierarchies, multiples etc

- id - incrementing primary key
- name - String
- slug - String (url)
- parent
- created_at
- created_by
- updated_at
- updated_by

## PostCategory

many-to-many relations for Posts & Categories

** Questions:** 
 * do we need timestamps here?

**Permissions:** add # to post #, remove # from post #

- post_id
- category_id

## User

**Note:** has no concept of username

- id - incrementing primary key
- first_name
- last_name
- slug - String (url) - generated from some sort of display_name function
- email_address
- profile_picture
- cover_picture
- bio
- url
- [admin defined user fields]
- created_at
- created_by
- updated_at
- updated_by

## Settings

Don't want this to become too much of a free for all. 
Question: is it useful to have a 'type' field? So that we could group certain settings together, for example all the settings needed by the frontend on every page.

- id - incrementing primary key
- key - String
- value - Text
- created_at
- created_by
- updated_at
- updated_by

## Image

##PostImage
      


# ACL
## Roles

Quick version of initial roles would be:

- **admin** - all perms, 
- **author** - post related perms only, 
- **guest** - same as author, potentially can't publish, won't show in standard list of users, 
- **subscriber** - gets notifications - relies on email - perhaps should be done through 3rd party service or not count as a user but something else?. 
- **none** - someone who tried to register and never got accepted
- not sure if there is a need for any other type of user right now? I'm not sure what a user or reader is, or where to draw the line between authors and editors... especially when considering more advanced workflows for the future

## Permissions

X = user or role
Y = object in question (post, category etc)
Z = secondary object

* X can browse posts Y - special case that there are no posts X can browse?
* X can read post Y
* X can create post
* X can edit posts Y
* X can change state of post Y to Z
* X can delete post Y

## UserRoles
## UserPermissions
## RolePermissions