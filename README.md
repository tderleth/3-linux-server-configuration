# Project: Linux Server Configuration

This repo is part of a series of projects belonging to my Full Stack Web Developer Nanodegree. Purpose of this lesson is to dig deeper into web application hosting, interactions between multiple systems and Linux security.

## Instance

| property   | value                              |
| :--------- | :--------------------------------- |
| IP address | 63.32.57.102                       |
| port       | 2200                               |
| URL        | <http://udacity.thomasderleth.de/> |

### Login

| User   | Command                                                        |
| :----- | :------------------------------------------------------------- |
| ubuntu | `ssh ubuntu@63.32.57.102 -p 2200 -i {path-to-private-key.pem}` |
| grader | `ssh grader@63.32.57.102 -p 2200 -i {path-to-private-key}`     |

_(Grader private key secret is literally secret.)_

## Command history

```bash
### Update server

# update list of packages
sudo apt-get update 
# upgrade packages
sudo apt-get upgrade


### Secure server

# change port to 2200
sudo nano /etc/ssh/sshd_config 				
# restart service to pick new port
sudo service sshd restart 				
# Deny all incoming connections		
sudo ufw default deny incoming 	
# Allow all outgoing connections			
sudo ufw default allow outgoing 		
# Allow ssh on port 2200	
sudo ufw allow 2200/tcp						
# Allow connections on port 80 using http			
sudo ufw allow www										
# Allow ntp connections
sudo ufw allow ntp								
# Enable ufw
sudo ufw enable


### Grader account & access

# Add new user named grader
sudo adduser grader
# grant grader user sudo permissions
sudo cp /etc/sudoers.d/90-cloud-init-users /etc/sudoers.d/grader
sudo nano /etc/sudoers.d/grader
# Install public key 
sudo mkdir /home/grader/.ssh
echo {public_key_content} > /home/grader/.ssh/authorised_keys
# Change permissions on ".ssh" directory
sudo chmod 700 .ssh
# Change permissions on "authorised_keys" file
sudo chmod 644  /home/grader/.ssh/authorised_keys
# Change "PasswordAuthentication yes" in "/etc/ssh/sshd_config"
sudo nano /etc/ssh/sshd_config
# Restart ssh service
sudo service ssh restart
# Check if login works from localhost
ssh grader@63.32.57.102 -p 2200 -i {path-to-private-key}


### Prepare to deploy the project

# Configure the local timezone to UTC.
sudo timedatectl set-timezone UTC
# Install apache2 
sudo apt-get install apache2
# Install mod-wsgi
sudo apt-get install libapache2-mod-wsgi
# Configure Apache to handle requests using the WSGI module (add "WSGIScriptAlias / /var/www/html/run.py" to conf)
sudo nano /etc/apache2/sites-enabled/000-default.conf
# Restart apache 
sudo apache2ctl restart
# Install PostreSQL 
sudo apt-get install postgresql
# Create database user 
sudo -u postgres createuser catalog
# Login to PostgreSQL command-line interface
sudo -u postgres psql
# Check if user was created
\du
# Create database 
sudo -u postgres createdb catalog
# Login to PostgreSQL command-line interface
sudo -u postgres psql
# Check if database was created
\l
# Login to PostgreSQL command-line interface
sudo -u postgres psql
# Grant access rights
grant all privileges on database catalog to catalog;


### Deploy Todo List project

# adjust folder permissions to clone into this folder
sudo chmod 777 /var/www/html
# Change to html folder
cd /var/www/html
# clone repo
git clone https://github.com/tderleth/2-item-catalog.git .
```

### Get server

-   [x]  Start a new Ubuntu Linux server instance on [Amazon Lightsail](https://aws.amazon.com/de/lightsail/).
-   [x]  Follow the instructions provided to SSH into your server.

### Secure server

-   [x]  Update all currently installed packages.
-   [x]  Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.
-   [x]  Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).

### Grader access

-   [x]  Create a new user account named grader.
-   [x]  Give grader the permission to sudo.
-   [x]  Create an SSH key pair for grader using the `ssh-keygen` tool.

### Prepare to deploy the project

-   [x]  Configure the local timezone to UTC.
-   [x]  Install and configure Apache to serve a Python `mod_wsgi` application.
-   [x]  Install and configure PostgreSQL (Create a new database user named catalog that has limited permissions to your catalog application database).
-   [x]  Install git.

### Deploy Todo List project

-   [x]  Clone and setup your Todo List project from the Github repository you created earlier in this Nanodegree program.
-   [ ]  Set it up in your server so that it functions correctly when visiting your server’s IP address in a browser. (Docs: <http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/>)
-   [ ]  Make sure that your .git directory is not publicly accessible via a browser!

## Third-party resources

-   [Ubuntu](http://releases.ubuntu.com/16.04/)
