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

To validate server, from the browser using the localhost or publicIP.




