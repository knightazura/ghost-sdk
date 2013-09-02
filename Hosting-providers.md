[work in progress]

Notes on experiences with Node.js Platform providers.

## Azure

Pros:

* Free 1-month trial
* Easy set-up for a simple Node project: http://www.windowsazure.com/en-us/develop/nodejs/tutorials/create-a-website-(mac)/

Cons:

* When deploying from the Ghost repo (either locally, or by linking to GitHub), the deployment will error when initializing submodules.
    * This currently occurs because the casper theme is a submodule, and the submodule is linked to a private repo. See: http://social.msdn.microsoft.com/Forums/windowsazure/it-IT/9ffecee2-e0ee-4766-b5ce-b060e4a9d91d/deployment-error-bitbucket
    * When using a nightly build, casper is included and the submodule dependency does not apply.  Creating a local repo from a nightly build and pushing directly to Azure works, until Azure tries to install the node dependencies.  It bugs out when trying to compile sqlite3. See the error msgs below:

```
remote: Building the projects in this solution one at a time. To enable parallel build, please add the "/m" switch.
remote: MSBUILD : error MSB3428: Could not load the Visual C++ component "VCBuild.exe". To fix this, 1) install the .NET Framework 2.0 SDK, 2) install Microsoft Visual Studio 2005 or 3) add the location of the component to the system path if it is installed elsewhere.  [C:\DWASFiles\Sites\testghost\VirtualDirectory0\site\wwwroot\node_modules\sqlite3\build\binding.sln]
remote: gypnpm ERR! sqlite3@2.1.14 install: `node-gyp rebuild`
remote: npm ERR! `cmd "/c" "node-gyp rebuild"` failed with 1
remote: An error has occurred during web site deployment.
remote: npm ERR!
remote: npm ERR! Failed at the sqlite3@2.1.14 install script.
remote: npm ERR! This is most likely a problem with the sqlite3 package,
remote: npm ERR! not with npm itself.
remote: npm ERR! Tell the author that this fails on your system:
remote: npm ERR!     node-gyp rebuild
remote: npm ERR! You can get their info via:
remote: npm ERR!     npm owner ls sqlite3
remote: npm ERR! There is likely additional logging output above.
remote:
remote: npm ERR! System Windows_NT 6.2.9200
remote: npm ERR! command "D:\\Program Files (x86)\\nodejs\\0.10.5\\node.exe" "D:\\Program Files (x86)\\npm\\1.2.18\\bin\\npm-cli.js" "install" "--production"
remote: npm ERR! cwd C:\DWASFiles\Sites\testghost\VirtualDirectory0\site\wwwroot
remote: npm ERR! node -v v0.10.5
remote: npm ERR! npm -v 1.2.18
remote: npm ERR! code ELIFECYCLE
remote: npm
remote:
remote: Error - Changes committed to remote repository but deployment to website failed, please check log for further details.
```


## Modulus.io https://modulus.io/

Pros:

 * Dead simple web-based deployments (just click 'Upload' and send the Ghost-build.zip). Weekly/Nightly builds work, too. Make sure the node_modules folder is **not** included though, unless your system is 64-bit linux.
 * Nice Web interface for monitoring, stats, and viewing logs. 
 * Really simple project setup (not bogged down with menus and stuff to click like EC2 or Azure)
 * Persistent cloud storage that can be shared by Node instances
 * Node environment variables can be set via the web interface. Also NODE_ENV is set to 'production' by default.

Cons: 

Only one really - no access to the filesystem.  Currently, deploys are all or nothing, and the entire deployment is dropped when a new one occurs. This means that by default, the 'content' folder and the sqlite database get deleted any time a new version of Ghost is deployed. You can't just upload a file or two and restart the application.

There is, however, persistent file storage available in /app-storage (env. variable: CLOUD_DIR).  This would be an ideal location for the 'content' folder, as it could be shared among multiple instances of ghost, or a single instance scaled across multiple "Servos".  See https://modulus.io/codex/projects/file_storage

One would think the SQLite database file could also be placed in /app-storage, but for some reason it cannot.  Doing so just causes a bunch of Node/SQLite errors to occur when Ghost runs for the first time.  Customer support didn't really have an answer as to why an SQLite DB could not be stored in /app-storage other than "It's not SQLite friendly". 

** Possible Solutions**

Modulus support did make mention of "graceful shutdown" events that could be used to take a backup of the database before re-deploying.  See https://modulus.io/codex/projects/graceful-shutdown
It may be possible to hook into the Ghost API to do a site dump just before a 'stop' event, and then do an import after a 'deploy' event. Currently, there is a 2 second time limit between the 'stop' event and application shutdown. So if the site is large and requires more than 2 seconds for a dump, then the dump will get cut off.  Manually backing up and restoring appears to be the only real solution to the database issue at this time.

As for the 'content' folder, Ghost would need to have a way to map it to /app-storage/content, or CLOUD-DIR/content.  

Modulus support is available to chat in #modulus on Freenode.  They also made mention that incremental updates (changing files without a complete deploy) is on their roadmap, but did not specify when it would be ready.