# Apache-proxy-VM-
Linux Apache proxy setup on Virtual Host in Ubuntu
## Installation commands and config changes
### Apache Installation commands  on Ubuntu 20.04
Apache comeup by default in the Ubuntu default repositories and it can be possible to install using package management tools. The Appache HTTP server is most widely used server.

Before. Installating we should create a user and give sudo privileges to install and configured on the server.

Here, are the list of the Commands to install and configure the Apche server.

Before, installing any software better to update the pacakges with latest changes with.


> sudo apt update


Later, install the apache2 package and it will install all the dependencies.


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

**To protect the server from the outside, firewalls have to be installed and kept in a running state with the specified port number.**

> sudo apt install firewall* -y

To check the status of the firewall.

> sudo systemctl status firewalld

To start and enable the serviceusing.

> sudo systemctl start firewalld

> sudo systemctl enable firewalld

For serving on the specified port, with security/firewall service can be enabled.

> sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent

> sudo firewall-cmd --zone=public --add-service=http --permanent

> sudo firewall-cmd --reload

#### To validate the installation
> apache2 -v

![APACHE](https://user-images.githubusercontent.com/38424194/149843666-9d18f939-933c-4032-9f96-c00f48d461d4.PNG)

To validate server, from the browser using the localhost or publicIP.
![apche-1](https://user-images.githubusercontent.com/38424194/149841014-8667abd5-1f4d-4340-a8bd-30b8b2532623.PNG)

## Nodejs and npm Installation commands from ubuntu repository

Run the following command to update the packages and install Nodejs and npm.
/var/www/html/nodejs

>sudo apt update

>sudo apt install nodejs npm

To intialise the package.jason and dependencies

> npm init 
> node hello.js or pm2 start hello.js

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

### protocal of the installation and configurations
To serve the clients from a single server for the multiple domains by using the default path /var/www/html or modified path in the directory.
1. Here, I wrote a **Hello world! application in nodejs** to test and run my helloworld application in the virtual host with default HTTP port 8080.
2. Given, the permissions to the file u/g/o to r/w/x.


![f1](https://user-images.githubusercontent.com/38424194/149846290-057b1a1e-26bc-452a-9fc2-fe18afe976b9.PNG)


![image](https://user-images.githubusercontent.com/38424194/149930866-3ecf3a7d-8067-49db-b21f-cd9072ca62ce.png)

### NOdejs dependences are installed in the same directory.

3. Here /var/www/html/nodejs we can run and check the status and for running the node application using the pm2.

> pm2 status hello.js

4. To serve the, application content on apache server So, the default configuration file has to be modified or copied with a new file to serve the client by changing/updating the host configurations.

![image](https://user-images.githubusercontent.com/38424194/149931550-e59c6711-c26e-4fa1-947e-c43289cb6fde.png)



![image](https://user-images.githubusercontent.com/38424194/149931698-7d74f226-3ecb-447c-84a7-582fc39ccdae.png)


Here, you can see the host configaration file

![image](https://user-images.githubusercontent.com/38424194/149938484-72d3683f-5a15-4b66-ad5d-85a1f45354ed.png)




5. To enable the proxy and proxy_http

> sudo a2enmod proxy
> sudo a2enmod proxy_http
> sudo a2enmod ssl
> sudo a2enmod headers

6. To save the changes and makes the configuration avilable to the host.

> sudo a2ensite host.conf (file.conf)

7. Disable the **000-default.conf** config file.

> sudo a2dissite 000-default.conf

8. Test the configuration errors.

> sudo apache2ctl configtest

9. To take all the changes into configuration files.

> sudo systemctl restart apache2
> 


Now, it can server the our application on virtual host.

### Self signed certificate with openssl

> sudo openssl x509 -req -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt

> sudo a2ensite default-ssl

> sudo a2enconf ssl-params

> sudo systemctl restart apache2

![cert](https://user-images.githubusercontent.com/38424194/149853471-50aaea64-5901-4e5d-a857-78a5761bfee7.PNG)


Here, you can the proxy pass from http://192.168.0.19 to https://192.168.0.19 with ssl
![local](https://user-images.githubusercontent.com/38424194/149929325-b8f2f8e9-5cda-45a6-b6ce-798443b86dd4.PNG)


![http](https://user-images.githubusercontent.com/38424194/149929357-66164c62-5ff5-4d03-8aa3-3fc1276046a3.PNG)


![https](https://user-images.githubusercontent.com/38424194/149929395-4ee71065-e75a-4a9c-ae18-a382343f1068.PNG)


###  Ports
Here, I used defalut port for apache localhost http://127.0.0.1:8080 for proxy pass and request to redirect to https://192.168.0.19 on port 443 with ssl protocal for (https) certification.

![image](https://user-images.githubusercontent.com/38424194/149937817-00aacb5b-2a76-4260-b9a2-19584085011b.png)


![image](https://user-images.githubusercontent.com/38424194/149938085-7d99a5f6-d455-4971-9db0-fe921980c31f.png)


