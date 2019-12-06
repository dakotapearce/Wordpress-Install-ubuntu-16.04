# Wordpress-Install
Install wordpress on a unbuntu server v18.04

## Overview ##
This is a complete guide to install wordpress via the unbuntu version 18.04 server. First off you will have to already had unbuntu 18.04-server installed, and have a internet conection set up through the server. It is also recommended that you install openssh by running these commands.

    sudo apt-get update
    sudo apt-get install openssh-server
   
That will update the repos and dowload openssh-server. After that's finished enter in the command bellow to configure your openssh,

    sudo nano /etc/ssh/sshd_config

Change the following lines

    Port 22
    PermitRootLogin yes
    #StrictModes yes
    
Save and exit the file then type 

    ifconfig
    
And write down your inet address,After your done all that then you can enter in anywhere from the command prompt by using this command,

    ssh user_name@your-inet -p 22

And your in!
    
## Step 1, Installing Apache ##
To start off we'll need apache2 to get online into the internet 

Update your local package.

    sudo apt-get update
    
Install the apache2 package, and enter yes finish installing.

    sudo apt-get install apache2 
    
After it should be all finished intalled 

## Step 2, Installing MYSQL ##
Now we need mysql to hold our wordpress database.

Install MYSQL server and it yes when prompted.

    sudo apt-get install mysql-server
    
after loading through the command you'll hit a screen that looks a little like this 

![Example One](/images/img1.png)




