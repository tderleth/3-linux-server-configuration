# Project: Linux Server Configuration

This repo is part of a series of projects belonging to my Full Stack Web Developer Nanodegree. Purpose of this lesson is to dig deeper into web application hosting, interactions between multiple systems and Linux security.

## Instance

| property   | value        |
| :--------- | :----------- |
| IP address | 63.32.57.102 |
| port       | 2200         |
| URL        | 63.32.57.102 |

### Login

| User   | Command                                            |
| :----- | :------------------------------------------------- |
| Ubuntu | `ssh -i "udacity.pem" ubuntu@63.32.57.102 -p 2200` |

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
```

### Get server

-   [x]  Start a new Ubuntu Linux server instance on [Amazon Lightsail](https://aws.amazon.com/de/lightsail/).
-   [x]  Follow the instructions provided to SSH into your server.

### Secure server

-   [x]  Update all currently installed packages.
-   [x]  Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.
-   [x]  Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).

### Grader access

-   [ ]  Create a new user account named grader.
-   [ ]  Give grader the permission to sudo.
-   [ ]  Create an SSH key pair for grader using the `ssh-keygen` tool.

### Prepare to deploy your project

-   [ ]  Configure the local timezone to UTC.
-   [ ]  Install and configure Apache to serve a Python `mod_wsgi` application.
-   [ ]  Install and configure PostgreSQL (Create a new database user named catalog that has limited permissions to your catalog application database).
-   [ ]  Install git.

### Deploy Todo List project

-   [ ]  Clone and setup your Todo List project from the Github repository you created earlier in this Nanodegree program.
-   [ ]  Set it up in your server so that it functions correctly when visiting your server’s IP address in a browser. 
-   [ ]  Make sure that your .git directory is not publicly accessible via a browser!

## Third-party resources

-   [Ubuntu](http://releases.ubuntu.com/16.04/)
