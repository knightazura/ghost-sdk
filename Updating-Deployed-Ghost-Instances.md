If you are on a version of Ghost which is from before the import/export UI was introduced in https://github.com/TryGhost/Ghost/commit/2b7d0f054d59cfb47735fe3845f00515d1a0f036 (23rd June) you will first need to update to this version so that you can export your data.

## Getting the import/export UI:
* Navigate to the place where you keep your deploy script, update the deploy script with the latest version: https://gist.github.com/ErisDS/6f32e9b75d08a1c81f9b
* run the deploy script with `--refspec 6f32e9b75` to deploy this exact commit. (You may have to run git fetch   first)
* *Note* The deploy script tends to fail to restart ghost, if this happens, login to your EC2 and do it manually

## Exporting your data
* In your Ghost admin panel, navigate to `/ghost/debug`
* Click 'export' - a download will start automatically

## Fixing the data
* For every post in the export, you need to change the key `content` to `content_raw` and then change `content_html` to `content`. 
* Keep your exported and fixed json file somewhere safe

## Updating to the latest Ghost
* Run the deploy script again, but this time with the default refspec (master). 
* Go to /ghost/login, register a new user as usual and login (note: this is your login from now on, it won't get overridden with the old data)
* Delete any fixtures you don't want
* Navigate to `ghost/debug`
* Choose import and import your fixed json file

Hopefully, everything worked and you now have your posts back