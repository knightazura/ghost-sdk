(This is very much a work in progress)

## Posts

- id - incrementing primary key
- title - String
- slug - String (url)
- content - Text
- content_html - Text
- featured - Boolean
- image 
- status
- language
- created_at
- created_by
- updated_at
- updated_by
- published_at
- published_by 

## Category

- id - incrementing primary key
- name
- parent

## Post Category

- post_id
- category_id

## User

**Note:** has no concept of username

- id - incrementing primary key
- first_name
- last_name
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

- id - incrementing primary key
- key - String
- value - Text
- created_at
- created_by
- updated_at
- updated_by
      