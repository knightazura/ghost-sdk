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