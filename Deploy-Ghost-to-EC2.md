## How to setup an EC2 instance

1. Create an AWS account if you don't already have one. This requires you to login to http://aws.amazon.com/ with your amazon username and password, and then enter credit card details. You shouldn't have to pay anything - we'll use a micro instance which is in the free tier.
1. Navigate through "My Account/Console" > "AWS Management Console" > "EC2", or just click here: https://console.aws.amazon.com/ec2/v2/home?region=us-west-2
1. Configure your default security group to have ssh, http, and https for all incoming IPs (don't forget to press apply at the end): http://docs.aws.amazon.com/gettingstarted/latest/wah-linux/getting-started-security-group.html
![Security Group Settings](http://i.imgur.com/W0IhW7x.png)
1. Get your key (.pem file) and save it in ~/.ssh http://docs.aws.amazon.com/gettingstarted/latest/wah-linux/getting-started-create-key-pair.html
1.  Hit "Launch Instance"
  - use the classic wizard
  - choose Ubuntu Server 12.04.2 LTS
  - change nothing on the Launch Instances, Advanced Instance Options, or Storage Device Configuration screens
  - on the Key-Value screen, enter a sensible name value
  - on the Key Pairs screen, choose the Key Pair you setup and saved earlier
  - on the Security Groups screen, choose the default security group that you updated earlier
  - Hit Launch! You should now have an ec2 instance. You should have a public DNS something like ``ec2-xx-xxx-xx-xx.[region].compute.amazonaws.com``. Your username will be **ubuntu**
1. Check everything is ok by sshing to the ec2 instance with the following command, and then exit
   -  ``ssh -i ~/.ssh/ghostdeploy.pem ubuntu@ec2-xx-xxx-xx-xx.[region].compute.amazonaws.com``

## Configuring EC2 for Ghost
1. Save the [config script](https://gist.github.com/ErisDS/b75be8bfe12c337a17bb) somewhere on your machine which is easy to find.
1. Send the config file to ec2 with the following command:
  -  ``scp -i ~/.ssh/ghostdeploy.pem /path/to/ghost-ec2-config.sh ubuntu@ec2-xx-xxx-xx-xx.[region].compute.amazonaws.com``
1. ssh into the ec2 instance again
1. run:
  - ``sudo ./ghost-ec2-config.sh``
1. create a file in /var/www/app.js - I used the default node.js hello world code: http://nodejs.org/#column1
1. navigate to your ec2 in a browser (ec2-xx-xxx-xx-xx.[region].compute.amazonaws.com) and you should see "Hello World"

## Deploying Ghost to EC2
1. You will need an empty directory somewhere on a machine with the following pre-requisites:
  - git cli installed with a github ssh key setup
  - ruby, ruby sass and ruby bourbon installed
  - ghostdeploy.pem saves in ~/.ssh
1. Save the [ghost-deploy.sh](https://gist.github.com/ErisDS/6f32e9b75d08a1c81f9b) script in your empty directory
1. Run the script. It takes a number of arguments:
  * ``-f | --fork [TryGhost]``   - which fork of Ghost to deploy. 
  * ``-r | --refspec [master]``  - which refspec (branch, tag, commit) to deploy. 
  * ``-s | --server [test1]``    - which server to deploy to. Options are staging, next, test1, test2, test3 or your own ec2 specified by the unique number and region like "ec2-54-214-216-43.us-west-2"
  * ``-p | --pem [ghostdeploy]`` - name of the pem file to use to authenticate
  * ``-c | --clean [false]``     - delete the clone after deploying

E.g. 
``./ghost-deploy.sh --server ec2-54-218-37-106.us-west-2 --pem ec2key`` would deploy TryGhost master to my own ec2 instance with my key

``./ghost-deploy.sh --server staging`` would deploy the latest master to staging, providing I have the ghostdeploy.pem file for the ghost servers in .ssh

``./ghost-deploy.sh --fork ErisDS --refspec my-branch --server test1 --clean`` would deploy my-branch from my own fork to the test1 server and then delete the local clone on my machine, providing I have the ghostdeploy.pem file for the ghost servers in .ssh