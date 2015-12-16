Docker dev-in-the-box

====================================================
This project contains my dev-in-a-box environment which has now been completely dockerized. I'll add more containers to this project when I get time. 

Currently I've dockerized 3 containers - 
* AWS DynamoDB local
* memcached
* Tomcat 8.0.30 with debug mode enabled

![devinbox.png](./images/devinbox.png)

These containers are using docker-compose vagrant plugin to run as lxc-docker containers. Use the following command to install the vagrant docker-compose plugin

```bash vagrant plugin install vagrant-docker-compose```

To get started simply execute - 
```bash 
vagrant up```

To inspect docker containers - 
```bash 
vagrant ssh
docker ps
```
