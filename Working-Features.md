* Dashboard
	* new post link
* Admin menu
	* G, dashboard, content, new post & settings menu items go to correct pages
* Content screen
	* Lists all posts with correct titles (incorrect time etc)
    * Select post in list highlights that post and opens it in the preview pane
* Write screen
	* Live preview works for all standard markdown
    * Save draft button saves entered title & content. Everything is published by default.
    * Editing/opening existing post puts correct info in title and content panels & save updates content.
* Database
	* The database is created and populated with basic data on first run of the server
    * New posts and edits save and last forever
    * The data can be reset by opening data/datastore.db and emptying the file. The next restart of the server will cause the database to be recreated and repopulated.
* Frontend
	* Homepage lists a number of posts as configured in config.js
    * Clicking on an individual post loads an individual post page
    * Date formatting helper uses moment