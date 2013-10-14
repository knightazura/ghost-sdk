One of the questions we get asked the most is (when) will Ghost do X?

We have a list of features that we plan to implement which is as long as a gorilla's arm, and it's hard to communicate. This list attempts to quantify that list, detail the finer points where we know them, and will be expanded upon as it becomes clearer how a feature will fit into Ghost. 

If you're looking to figure out whether or not a feature will be implemented, the principles are:

- Is it a feature that is fundamentally core to publishing digital content? If yes, then it will probably be in Ghost core. E.g I18n, post scheduling, etc.
- Is it something so large and complex that other companies have entire teams and infrastructures dedicated to it? Then it will probably be provided through 3rd party integrations. E.g. Comments, and media management.
- Is it something that is only relevant to a small group, or for a short time? If yes, it's probably plugin territory. E.g. XML-RPC, Import tools

### Localisation
Note: Ghost core will contain the tools for making Ghost work in various languages, but the languages and settings specific to different languages will be provided via a 'language pack'.
* date localisation
* advanced character sets
* translatable admin
* post language
* multi-language blog posts

### Blog content creation
* Extended markdown features (Haunted Markdown)
* Post scheduling
* Post queue
* Auto-save & offline
* Post cover / feature image
* Multiple image sizes
* Video embedding
* Version control

### Site structure
* Static Pages
* Navigation menu UI
* Different permalink structures
* Support for installing Ghost in a subdomain

### Users
* Multiple users
* User management screen
* User role and permission management
* User profile pages

### Plugins & integrations
- Basic plugin API / structure
- Hooks for interacting with Ghost
- Database API
- Routing API
- Dashboard widget API
- Admin UI hooks
- Authentication tools for working with 3rd parties
- API tools for interacting with 3rd party APIs
- Importer hooks, & improved import workflow
- Importer plugin (for WP, Tumblr, Blogger, etc)


