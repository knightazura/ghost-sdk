## Configuration

I would suggest that every app should have it's own `config.js` file that holds important App data.

```
{
	// App description
	displayname: 'Worpress Importer',
	identifier: 'wp-import'
	description: 'The Worpress Importer App ...',

	// App permissions
	permissions: {
		api.posts: ['create', 'edit'],
		api.settings: ['read'],
		helpers: ['create']
	}

	// App certification
        checksum: <hash of all app files>
	certification: base64(signature(<config.js values> + date))
}
```

### Permissions

Every App, that needs access to the API has to ask for permission using the `config.js` file. Upon activation a modal is presented asking the user if the App is allowed to use the required permissions. If the user declines the App won't be activated. Giving the user the option to deny certain permissions makes no sense in my opinion since the developer has added the permission on purpose. Denying a single permission would probably render the App useless. I think that the best place to enforce permissions is the Ghosts proxy object.

Permissions allowed in `config.js`:

- `read`: Apps can only view objects of this type.
- `create`: Apps can read and create objects of this type.
- `edit`: Apps can read and update objects of this type.
- `delete`: Apps can read, edit, and delete objects of this type.

An overview of permissions granted to an App should be available on the (App) settings screen.

### Certification

To establish a trustworthy marketplace for Apps, every App should be submitted for a review. This process should make sure that Apps are working as intended and don't harm the Ghost installation (overwrite files, read passwords, ...).

When an App successfully passes the review process a signature by the review authority should be added to the `config.js` file. Every Ghost installation should contain the public key to verify the signature. If the signature is valid an indicator (seal of approval) that the App is certified can be displayed on the App settings page.

Process to sign an App:

- Calculate a hash for all app files and store it in `config.js`
- Sign the values of `config.js` with a private key and store the signature in `config.js`
- Every Ghost installation can verify the signature using a public key

To make sure that the Ghost installation is holding the correct public key we should provide a checksum for official releases. This would lower the chance that the user is using a bogus distribution with a public key that would show harmful Apps as certified. 

## Routes

I think, that App routes should only live under `/ghost/apps/<app-id>/` where `<app-id>` is the identifier from `config.js`. This would provide a unique namespace for every App and prevent unnecessary clutter.