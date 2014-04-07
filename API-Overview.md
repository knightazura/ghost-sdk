This is an overview of how the Ghost API is structured and how the different modules interact with each other. It is an attempt to explain the recurring question of "What API are you talking about?". 

![Ghost API Overview](https://dl.dropboxusercontent.com/u/1338220/ghost/Ghost_API.png)

- JSON API (`/core/server/api/`): Is meant as the core abstraction layer to provide clear interfaces for all access to Ghosts internal data. The JSON API takes care of enforcing permissions and returns a JSON response for every call. Formatting and removal of security relevant data is done within the JSON API.

- Data Models (`/core/server/models/`): Access to the database uses bookshelf.js as ORM. Bookshelf enables the use of MySql, SQLite and postreSQL. The data models add data (author, created_by, ...) to the data objects that are finally saved to the database. As a rule of thumb, only operations that are related to data that is being stored should be executed within the data models.

- Email (`/core/server/mail.js`): Email functionality in Ghost is implemented using the nodemailer module. Emails can be sent using the JSON API.

- Config: Not implemented yet.

- Apps (`/core/server/apps/`): Apps are used to add new functionality to Ghost. Access to the JSON API for Apps is restricted by permissions. An App could ask for permissions to access certain parts of the JSON API upon installation. Apps should not have to directly access any other module to implement its functionality.

- Restful API (`/core/server/routes/`): The Restful API is used to expose the JSON API to publicly reachable end points. It is necessary to authenticate for using the restful API at the moment. The API will be protected by OAuth (or something similar) in the future, user authentication will then only be needed for certain user related end points.

- Ember Admin: Ember Admin uses the restful API to access Ghost.

- Handlebars helpers (`/core/server/helpers/`): Handlebars helpers are used to provide functionality to the templates rendered by the front end. JSON API is used to get data used by the templates.

- Front end: The front end is rendered using the theme and content from the database is added using the Handlebars templates.