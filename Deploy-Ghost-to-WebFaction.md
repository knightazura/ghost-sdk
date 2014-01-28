#### **Note:** These instructions are pre 0.3 and no longer work.

Setup a new account on http://webfaction.com - it needs to be a paid account, the free trial does not have access to the features which you will need to deploy Ghost.

## 0. Point a Domain at WebFaction

Either a root domain, with NS records to: 

    ns1.webfaction.com
    ns2.webfaction.com
    ns3.webfaction.com
    ns4.webfaction.com

Or an A-Record for a subdomain, pointed to the IP address of your server. I'll tell you where to find the IP address later.

## 1. Set Up Your Website + Application

In your WebFaction (WF) control panel, go to Domains/Websites > Websites. Click on "Add new website" and enter the following details:

* Name - any name for your blog, no spaces
* Domains - enter the domain you have pointed at WF
* Contents - Add an application > Create a new application

![step1-1](http://i.imgur.com/dqMGqWu.png)

You will now get a modal/popup, enter the following details

* Name - same as your blog name above, no spaces
* App category - Custom
* App type - Custom app (listening on port)

![step1-2](http://i.imgur.com/9M492d2.png)

Press Save to close the modal. Once it has closed, press save again to finish creating the website.

You should now see an overview of your applications, and if you are setting up a blog on a subdomain, you should be able to see the IP Address which you need to point your subdomain to in **Step 0** above.

![step1-3](http://i.imgur.com/ZYeM8xP.png)

### Get Your Port Number

In your WF control panel, go to Domains/Websites > Applications. 

You will now see a list of your applications - beside your new application you will see "Custom app (listening on port) (port #####) - **write down this port number somewhere, you will need it again in a minute**

![port](http://i.imgur.com/OkBOIGW.png)

## 2. Set Up Your Server

This is probably the hardest part, if you can get past this - you're golden.

### SSH Into Your Server

I'm going to assume you're on Mac or Linux. If not - follow [these](http://docs.webfaction.com/user-guide/access.html#connecting-with-ssh) instructions for Windows.

Open up Terminal.app - and get ready to love that sexy command line prompt. Enter the following:

`ssh username@username.webfactional.com` - where "username" is the webfaction username that you signed up with

Press enter. You should be prompted for a password. Enter your WebFaction account password.

You should now be at a new command prompt that looks something like

`[username@web123 ~]$`

### Install Node.js

Now, in the same place as you were at the end of the last step, enter the following (replace 'yourblogname' with the blog name you set up in step 1):

This will download Node.js onto your server

    cd ~/webapps/yourblogname
    mkdir src
    cd src
    curl http://nodejs.org/dist/node-latest.tar.gz | tar xz --strip-components=1

The next two commands will run the install.

    ./configure --prefix=$HOME
    make install

This part takes a while. Grab a cup of tea. Alternative, put Terminal in fullscreen mode, sit back in your chair, and pretend you're in The Matrix.

Once that is eventually finished, you can check Node.js is working properly by typing following command:

    node -v

It should return something like `v0.10.18`

And you should also have npm, the package manager for node, type:

    npm -v

It should return something like `v1.3.8` 

And now we can use NPM to install Forever, a utility which will keep your Ghost blog running... forever.

    npm install -g forever

Congrats. Your server is now prepped, and ready to rock. Keep this terminal window open, this is your **Remote Terminal** - you will need it again later.

## 3. Setting Up Ghost

Right! The good part. First make a place on your computer where you will keep your Ghost site. Your live website will always mirror these files. They will be identical. Unzip your Ghost package here.

### Edit config.js

Scroll down and ...

Replace all references to `url: 'http://my-ghost-blog.com'` with `http://yourdomain.com` from **Step 0**

Replace all references to port **2368** with the port number you wrote down in **Step 1** above. 

Save and close the file.

### Build & Deploy Ghost

Open up a new terminal window. This one is your **Local Terminal** - don't get the two confused!

    cd ~/path/to/your/ghost

Next we're going to install grunt, a tool which will help us get Ghost deployed

    npm install -g grunt-cli

Now we're going to install Ghost locally

    npm install

If you get errors, try `sudo npm install`

Now build a Ghost package to deploy to your server

    grunt build

Now let's send that zip file to your server - make sure you edit the following command to include your WF username, and your blogname (from **Step 1**) at the end.

    scp .dist/build/Ghost-Build.zip username@username.webfactional.com:~/webapps/blogname

### Install Ghost

Now switch to your **Remote Terminal** and run

    cd ~/webapps/yourblogname
    unzip -uo Ghost-Build.zip
    rm -rf Ghost-Build.zip

Now we do the install

    npm install

and finally, we start up Ghost

    forever start index.js

Navigate to your chosen domain, and you should see a working blog. If not - you fucked something up - start again.