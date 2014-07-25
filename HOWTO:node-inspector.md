# Using node-inspector during Ghost development

### What is "node inspector"
> Node Inspector is a debugger interface for Node.js applications that uses the Blink Developer Tools (formerly WebKit Web Inspector).

Basically, it is an awesome tool to make debugging Node easy and (relativly) painless.
You can read more about it on their official page: https://github.com/node-inspector/node-inspector

### Awesome, so how do I use this with Ghost?
- install node-inspector by running the following command: ```npm install -g node-inspector```
- open the Gruntfile.js and look for the ```grunt-express-server``` task configuration (at the time of writting this, line 99)
- in the "options" section of the "dev" config, add the property ```debug: true```. this will start the node proces in debug mode (equivilent do doing ```node --debug```)
- your updated config should look something like this:
```
// ### grunt-express-server
// Start a Ghost expess server for use in development and testing
express: {
    options: {
        script: 'index.js',
        output: 'Ghost is running'
    },

    dev: {
        options: {
            debug: false
        }
    },
    test: {
        options: {
            node_env: 'testing'
        }
    }
},
```

- open your terminal and run the usual ```grunt dev```
- now in another termianl window, run ```node-debugger```
  - if you get an error about port 8080 being in use, re-run the above command with the ```--port=####``` flag to change the port
- once node inspector starts up, it will automatically open your default browser
  - something else to note is that node-inspector only works with Chrome and Opera (sorry FireFox and IE users). So if one of those are your default browser, the you will have to copy the URL and open it in a compatable browser.
- now you are ready to say goodbye to abusing console.log and start doing some awesome visual and interactive debugging!
  - just like with any in-browser debugging tool, you can set breakpoints and interact with  in-scrop variables from the console
  - for more in-depth documentation of what you can do, you can check out [Working with the console](https://developer.chrome.com/devtools/index#console) and [Debugging JavaScript](https://developer.chrome.com/devtools/index#debugging-javascript) in the Chrome Dev Tools documentation.

### What next?
Now go forth and be awesome. Developing in Node will never be the same :-)
  