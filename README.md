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

Enter in a new root password and write it down, we will need this later.

Now we will create a user and database for wordpress, type 

    mysql -u root -p
    
you'll be propmted to enter your password make sure its the one we wrote down before.

Now we are in mysql command line and will create a user and database for wordpress, first we'll enter

    CREATE USER 'new_user'@'localhost' IDENTIFIED BY 'new_user_password';
    
MAKE SURE YOU WRITE THE USERNAME AND PASSWORD DOWN! you need this for your config later.
Then we create a database and grant permissions to the database, then we'll be finished in mysql for now.

    CREATE DATABASE wordpress;
    GRANT ALL PRIVILEGES ON *.* TO 'new_user'@'localhost';
    exit

## Step 3, Installing PHP ##

This is a very easy step, enter in these commands and everything should be configured for you just hit yes to install.
   
    sudo apt-get install php
    sudo apt-get install php-{bcmath,bz2,intl,gd,mbstring,mcrypt,mysql,zip} 
    sudo apt-get install libapache2-mod-php7.0
    
## Step 4, downloading and Configuring Wordpress ##

First were going to grab the wordpress zip file and unzip in our root directory, sugested is the html file in /var/www/html. Then we'll download the wordpress package and unzip 
First we need to give ourselves root permissions to the directory 

    sudo chown -R your-server-username:your-server-username /var/www/html
    cd /var/www/html
    sudo rm index.html
    
Then lets grab wordpress and unzip the directory 

    sudo wget http://wordpress.org/latest.tar.gz
    sudo tar xfz latest.tar.gz

Then we'll move the files from wordpress directory into the current directory which sould be /var/www/html

    mv wordpress/* ./
    sudo rm latest.tar.gz
    sudo rm -r wordpress
    
Now we can head to the ip address or domain on your browser to do the wordpress install  
    
## Step 5, Wordpress install ##
    
First screen will pop up,cler just continue the installation 

![Example Two](/images/img2.png)

Next were going to enter in some information, including database name, myslq user created before with password, look closely at the feilds to help with what the requirements are.

![Example Three](/images/img3.png)
   
With the next screen we well need to head back to the terminal for a second and enter in a couple commands. First we'll need to go to the directory like we did before 

    cd /var/www/html
    
now were gonna create and edit a config file use the command bellow to create and edit the file  
    
    sudo nano wp-config.php
    
Then copy and paste the information from your wordpress screen that's highlighted bellow
   
![Example Four](/images/img4.png)  

make sure the document looks like this 

![Example Six](/images/img7.png)

After your document looks aok then save and exit by using CTRL-O {ENTER} then CTRL-X 

After your hit run the installation button, when you hit a page that looks a little like this you're all done 

![Example Five](/images/img5.png) 

hit the login but login with the credintials before and your ready to start wordpressing.

