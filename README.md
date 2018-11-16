# Project: Linux Server Configuration

This repo is part of a series of projects belonging to my Full Stack Web Developer Nanodegree. Purpose of this lesson is to dig deeper into web application hosting, interactions between multiple systems and Linux security.

## Instance

| property   | value        |
| :--------- | :----------- |
| IP address | 63.32.57.102 |
| port       | 22           |
| URL        | 63.32.57.102 |

## Summary

### Get server

-   [x]  Start a new Ubuntu Linux server instance on [Amazon Lightsail](https://aws.amazon.com/de/lightsail/).
-   [x]  Follow the instructions provided to SSH into your server.

### Secure server

-   [x]  Update all currently installed packages.
-   [ ]  Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.
-   [ ]  Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).

_Warning: When changing the SSH port, make sure that the firewall is open for port 2200 first, so that you don't lock yourself out of the server. When you change the SSH port, the Lightsail instance will no longer be accessible through the web app 'Connect using SSH' button. The button assumes the default port is being used. There are instructions on the same page for connecting from your terminal to the instance. Connect using those instructions and then follow the rest of the steps._

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
