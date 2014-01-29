Ghost imports from existing blogs by having them export a JSON file and then reading that in.

## Existing Plugins to Automate this:

### Official
* WordPress users can use the [Ghost WordPress Plugin](http://wordpress.org/plugins/ghost/) to export their data.

### Non-official
* Jekyll users can use the [Jekyll to Ghost Plugin](https://github.com/redwallhp/Jekyll-to-Ghost)

## Importing the JSON
Once you've generated the JSON go to `/ghost/debug` on your blog to access the import form.


## Rolling your own.

If no export tools exist for your current blogging system you'll need to create one that generates a JSON file that resembles the following. Please note that it should have no linebreaks, comments, or indentation in the final format. Those are only included here for readability and explanatory purposes.

	{
		"meta":{
			"exported_on":1388805572000,
			"version":"000"
			// epoch time in milliseconds
		},
		"data":{
			"posts":[
				// a list of hashes, each describing 
				// a post.
				{
					"id":5,
					"title":"my blog post title",
					"slug":"my-blog-post-title"
					"markdown":"the *markdown* formatted post body",
					"html":"the <i>html</i> formatted post body",
					"image":null
					"featured":0, // boolean indicating featured status?
					"page":0, // boolean indicating if this is a page or post
					"status":"published",
					"language":"en_US",
					"meta_title":null,
					"meta_description":null,
					"author_id":1, // the first user created has an id of 1
					"created_at":1283780649000,
								// epoch time in millis
					"created_by":1, // the first user created has an id of 1
					"updated_at":1286958624000,
								// epoch time in millis
					"updated_by":1, // the first user created has an id of 1
					"published_at":1283780649000,
								// epoch time in millis
					"published_by":1 // the first user created has an id of 1
				}
			],
			"tags":[
				// an array of hashes describing each 
				// tag in the system.
				{
					"id":3, 
					"name":"Colorado Ho!", 
					"slug":"colorado-ho", 
					"description":""
				}
				{
					"id":4,
					"name":"blue",
					"slug":"blue",
					"description":""
				}
			],
			"posts_tags": [
				// an array of hashes associating each 
				// tag with a particular post. 
				// if a tag is on multiple posts
				// it gets multiple entries here
				{"tag_id":3, "post_id":5}
				{"tag_id":3, "post_id":2}
				{"tag_id":4, "post_id":24}
			]
			
			// Ghost also has support for importing
			// users, roles, roles_users, permissions, 
			// permissions_users, permissions_roles
			// but none of these are required 
		}
	}
