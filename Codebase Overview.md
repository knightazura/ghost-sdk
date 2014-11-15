This is an overview of how the Ghost codebase is structured and how the different parts interact with each other. 

Conceptually, Ghost is made up of three different applications: 
- the JSON data API
- the client-side admin panel app which is built in Ember
- the server-side application which renders the blog with the active theme.

The diagram below shows how the three applications communicate with each other. It shows how both the API and the blog rendering lives server-side and so communicate via a simple `require()`, and the admin panel is a fully client-side application which communicates with the API over HTTP.

```
+-----------------------------------------------------------+
|                                                           |
|   +---------------------------------------------------+   |
|   |                                                   |   |
|   |                   JSON DATA API                   |   |
|   |                                                   |   |
|   +---------------------------------------------------+   |
|                   ^                    ^                  |
+-------------------|-------------+      |                  |
                    |             |      |                  |
               HTTP |             |      | require()        |
                    |             |      |                  |                                                                                                                                
+-------------------|------+      |      |                  |
|                   |      |      |      |                  |
|         Client    |      |      |      |   Server         |
|                   v      |      |      v                  |
|   +-----------------+    |      |    +----------------+   |
|   |                 |    |      |    |                |   |
|   |   Admin Panel   |    |      |    |      Blog      |   |
|   |   (Ember.js)    |    |      |    |     (theme)    |   |
|   |                 |    |      |    |                |   |
|   +-----------------+    |      |    +----------------+   |
|                          |      |                         |
+--------------------------+      +-------------------------+
```

Physically, Ghost is structured in two main folders:

* **content**  - contains the files which may be added or changed by the user such as themes and apps
* **core** - contains the core files which make up Ghost

### The `core` directory

The core directory is further split into four directories

* **client** - the client-side admin panel app, all code in here is written in ember
* **server** - server side code, which contains the API and models, plus all the helpers and code needed to render the blog frontend.
* **shared** - anything shared between the server and client
* **test** - various test suites

## Ghost Components In Detail

![Ghost API Overview](https://dl.dropboxusercontent.com/u/1338220/ghost/Ghost_API.png)

- JSON API (`/core/server/api/`): Is meant as the core abstraction layer to provide clear interfaces for all access to Ghosts internal data. The JSON API takes care of enforcing permissions and returns a JSON response for every call. Formatting and removal of security relevant data is done within the JSON API.

- Data Models (`/core/server/models/`): Access to the database uses bookshelf.js as ORM. Bookshelf enables the use of MySql, SQLite and postgreSQL via the knex query builder. The data models add data (author, created_by, ...) to the data objects that are finally saved to the database. As a rule of thumb, only operations that are related to data that is being stored should be executed within the data models.

- Email (`/core/server/mail.js`): Email functionality in Ghost is implemented using the nodemailer module. Emails can be sent using the JSON API.

- Config (`/core/server/config/`): Loads and validates the config file, and adds it to the base configuration which is then used throughout the server side code.

- Apps (`/core/server/apps/`): Apps are used to add new functionality to Ghost. Access to the JSON API for Apps is restricted by permissions. An App could ask for permissions to access certain parts of the JSON API upon installation. Apps should not have to directly access any other module to implement its functionality.

- Restful API (`/core/server/routes/`): The Restful API is used to expose the JSON API to publicly reachable end points. It is necessary to authenticate for using the restful API at the moment. The API will be protected by OAuth (or something similar) in the future, user authentication will then only be needed for certain user related end points.

- Ember Admin (`/core/client/`): The admin panel is written in Ember and uses the restful API to access Ghost

- Handlebars helpers (`/core/server/helpers/`): Handlebars helpers are used to provide functionality to the templates rendered by the front end. JSON API is used to get data used by the templates.

- Front end (`/core/server/controllers/frontend.js`): The front end is rendered using the theme and content from the database is added using the Handlebars templates.  All rendered content also passes through Express middleware functions.