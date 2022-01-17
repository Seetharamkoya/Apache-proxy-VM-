# Apache-proxy-VM-
Linux Apache proxy setup on Virtual Box _Ubuntu
## Apache Installation commands  on Ubuntu 20.04
Apache comeup by default in the Ubuntu default repositories and it can be possible to install using package management tools. The Appache HTTP server is most widely used server.

Before. Installating we should create a user and give sudo privileges to install and configured on the server.

Here, are the list of the Commands to install and configure the Apche server.

Before, installing any software better to update the pacakges with latest changes with.


> sudo apt update


later, install apache2 pacakge and it will install all the dependencies.


> sudo apt install apache2

After, the end of the installation check the server status weather it is running or not.

> sudo systemctl status apache2

To make sure serve continously it needs to be started and enable using.

> sudo systemctl start apache2

> sudo systemctl enable apache2

To stop the server.

> sudo systemctl stop apache2

When the Configuration are changed and to use those changes into effective by reloading.

>sudo systemctl reload apache2

**To ptotect the server from the outside firewalls has to be installed and keep them in a running state with the specified port number.**

> sudo apt install firewall* -y

To check the status of the firewall.

> sudo systemctl status firewalld

To start and enable the serviceusing.

> sudo systemctl start firewalld

> sudo systemctl enable firewalld

To serve the server on the specified port and service can be enabled.

> sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent

> sudo firewall-cmd --zone=public --add-service=http --permanent

> sudo firewall-cmd --reload

To validate the installation
> apache2 -v

![APACHE](https://user-images.githubusercontent.com/38424194/149843666-9d18f939-933c-4032-9f96-c00f48d461d4.PNG)

To validate server, from the browser using the localhost or publicIP.
![apche-1](https://user-images.githubusercontent.com/38424194/149841014-8667abd5-1f4d-4340-a8bd-30b8b2532623.PNG)

## Nodejs and npm Installation commands from ubuntu repository

Run the following command to update the packages and install Nodejs and npm.

>sudo apt update

>sudo apt install nodejs npm

it can install all the packages to complie and install native addons from npm.

To verify the installation by running:

> nodejs --version

![NODE](https://user-images.githubusercontent.com/38424194/149843962-c82bc057-777c-4775-87ed-59514fa8d046.PNG)


## Mongodb instllation

Run the following command to update the repositoty and pacakges with latest chanes and install MongoDb with the following commands.

> sudo apt update

> sudo apt install mongodb* y

It can install all the required packages like mongo-tools mongodb mongodb-clients mongodb-server mongodb-server-core.

To check the service status

> sudo systemctl status mongodb

To validate the installation 

> mongod --version


![NODE2](https://user-images.githubusercontent.com/38424194/149843986-06348da0-bad9-401c-94c1-61be3e6b6c2d.PNG)

