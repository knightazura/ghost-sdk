OAuth is an open standard for authorization. It provides protocols for client applications to obtain  permission to access a server resource on behalf of a user.

Ghost implements *OAuth 2.0 - Resource Owner Password Credentials Grant (RFC 6749, Section 4.3)* to allow a user to access a protected resource using username and password. The OAuth implementation essentially allows access tokens to be issued to the Ghost Admin, in exchange for valid user credentials. The Ghost Admin then uses the access token to access protected resources on the Ghost Server.

**Please note: OAuth 2.0 is only secure if you use an encrypted connection (SSL/TSL)!**

# Authentication flow


```
+----------+
|          |
|  User    |
|          |
+----------+
     v
     |     User
    (1) Credentials
     |
     v
+---------+                                  +------------+
|         |>--(2)--------- User ------------>|            |
|  Ghost  |             Credentials          |   Ghost    |
|  Admin  |                                  |   Server   |
|         |<--(3)------ Access Token -------<|            |
+---------+                                  +------------+
```
*Source: RFC 6749*

1. The user provides username and password
2. Ghost Admin sends a post request to obtain an access token:

    ```
    POST /ghost/api/v0.1/authentication/token
    Content-Type: application/x-www-form-urlencoded
    grant_type=password&username=<username>&password=<password>&client_id=ghost-admin
    ```
    - `grant_type`: name of the authentication type
    - `username`: email address
    - `password`: secret password
    - `client_id`: name of the client that is requesting access on behalf of the user
3. Ghost Server responds with access and refresh token

    ```
    {
        access_token: <access_token>
        refresh_token: <refresh_token>
        expires_in: 3600
        token_type: "Bearer"
    }
    ```
    - `access_token`: users access token; valid for 1 hour
    - `refresh_token`: users refresh token; valid for 24 hours
    - `expires_in`: validity of the access_token in seconds
    - `token_type`: access token type

# Usage

To access a resource on the server the access_token is sent as Authorization header.

```
GET /ghost/api/v0.1/users/me/
Authorization: Bearer <access_token>
```

The access token is stored in local storage and synchronized with all open windows. Token management is done using `ember-simple-auth`, a lightweight library that handles tokens and adds the authorization header to every request that is sent from Ghost Admin. If an access token is about to expire the refresh token is used to get a new access token without asking the user for its authentication credentials.

1. Ghost Admin sends a request to refresh an access token:

    ```
    POST /ghost/api/v0.1/authentication/token
    Content-Type: application/x-www-form-urlencoded
    grant_type=refresh_token&refresh_token=<refresh_token>&client_id=ghost-admin
    ```
    - `grant_type`: name of the authentication type
    - `refresh_token`: refresh token
    - `client_id`: name of the client that is requesting access on behalf of the user

2. Ghost Server responds with a new access token

    ```
    {
        access_token: <access_token>
        expires_in: 3600
        token_type: "Bearer"
    }
    ```
    - `access_token`: users access token; valid for 1 hour
    - `expires_in`: validity of the access_token in seconds
    - `token_type`: access token type

The refresh mechanism works as long as the refresh token is valid, after expiry the user has to sign in again.

# Ghost Implementation

Ghost only supports a very small set of OAuth features at the moment. The implementation is extensible and further authentication methods are going to be implemented in future releases.

Used Libraries:
- **oauth2orize** (https://github.com/jaredhanson/oauth2orize) is used for the backend implementation. It handles the generation of access tokens from the username and password using the  `oauth2orize.exchange.password` middleware and refreshing of an access tokens using the `oauth2orize.exchange.refreshToken` middleware.

- **ember-simple-auth** (https://github.com/simplabs/ember-simple-auth) is used to implement the resource owner password credentials grant for the client.