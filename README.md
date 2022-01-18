# Apache-proxy-VM-
Linux Apache proxy setup on Virtual Host in Ubuntu
## Installation commands and config changes
### Apache Installation commands  on Ubuntu 20.04
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

### Setting the virtual host configs on Apache 
To serve the clients from a single server for the multiple doomains by using the default path /var/www/html or modified path in the directory.
1. Here, I wrote a **Hello world! application in nodejs** to test our proxy request from the http to https in the virtual host with default HTTP port 8080.
2. Give, the permissions to the file u/g/o to r/w/x.


![f1](https://user-images.githubusercontent.com/38424194/149846290-057b1a1e-26bc-452a-9fc2-fe18afe976b9.PNG)


![f2](https://user-images.githubusercontent.com/38424194/149846310-ccc2e198-160d-41bf-b13f-c60fdabab7d2.PNG)


3. Here /var/www/html/nodejs we can run and check the status of the node application using the pm2.

> pm2 status hello.js

4. To serve the, application content on apache server So, the default configuration file has to be modified or copied with a new file to serve the client by changing/updating the host configurations.

![h2](https://user-images.githubusercontent.com/38424194/149848335-be659f68-f36c-41cd-8e92-daf2b5809123.PNG)


![image](https://user-images.githubusercontent.com/38424194/149848957-5fc1986e-8e8a-4c0f-a4cb-b9d8294b9c9d.png)


![h3](https://user-images.githubusercontent.com/38424194/149848386-af762306-5d6f-4961-8eba-1a3c61067192.PNG)

5. To enable the proxy and proxy_http

> sudo a2enmod proxy
> sudo a2enmod proxy_http

6. To save the changes and makes the configuration avilable to the host.

> sudo a2ensite host.conf (file.conf)

7. Disable the **000-default.conf** config file.

> sudo a2dissite 000-default.conf

8. Test the configuration errors.

> sudo apache2ctl configtest

9. To take all the changes into configuration files.

> sudo systemctl restart apache2


Now, it can server the our application on virtual host.

### Self signed certificate with openssl

> sudo openssl x509 -req -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt

![cert](https://user-images.githubusercontent.com/38424194/149853471-50aaea64-5901-4e5d-a857-78a5761bfee7.PNG)


![local](https://user-images.githubusercontent.com/38424194/149929325-b8f2f8e9-5cda-45a6-b6ce-798443b86dd4.PNG)


![http](https://user-images.githubusercontent.com/38424194/149929357-66164c62-5ff5-4d03-8aa3-3fc1276046a3.PNG)


![https](https://user-images.githubusercontent.com/38424194/149929395-4ee71065-e75a-4a9c-ae18-a382343f1068.PNG)




