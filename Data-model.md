(This is very much a work in progress)

## Posts

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
- created_at
- created_by
- updated_at
- updated_by
- published_at
- published_by 

## Category / Tag

Categoristion which supports hierarchies, multiples etc

- id - incrementing primary key
- name - String
- slug - String (url)
- parent

## Post Category

many - to - many relations for Posts & Categories

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

##Settings

Don't want this to become too much of a free for all. 
Question: is it useful to have a 'type' field? So that we could group certain settings together, for example all the settings needed by the frontend on every page.

- id - incrementing primary key
- key - String
- value - Text
- created_at
- created_by
- updated_at
- updated_by
      