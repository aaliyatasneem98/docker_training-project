<b><h1>Docker Project: Launching ownCloud via Docker Compose</h1></b>

<b>Overview:-</b>

This project is based on Docker technology and is created by integrating the technologies Linux RHEL8 (RedHat 8), Python3, Docker, MySQL etc. Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. OwnCloud is a self-hosted file sync and share server. It’s functionally similar to as DropBox, Google Drive etc. This gives us access to our data (files, calendars, contacts, mails etc) through a web interface, across all the devices.

Here, I have deployed the ownCloud architecture inside a docker container and have linked it to MySQL database which is also been deployed in another container. Using Docker Containers, it will be deployed using minimal RAM and in minimal time (within few seconds).

Both the containers are attached to persistent storage (volume) which has been created to ensure that there is no data loss in case of any system failure (crashing of containers or server i.e. been hosted on docker container due to load).

In this project, docker-compose is used through which we can set all environment in one single click by using one single file within a second.

No rush. No hustles !!


<b>Built with:-</b>
1.	Oracle Virtual Box
2.	RedHat Linux RHEL8
3.	Docker
4.	OwnCloud
5.	MYSQl


<b>Project Flow:-</b>
1.	Download and install Docker
2.	Start Docker Services
3.	Docker Compose installation (as it doesn’t come pre-installed with Docker)
4.	Create Containers for the server and database.
5.	Create Docker volume for persistent storage. This step is required because docker containers are by default ephermal in nature which leads to data loss in case of crash or system failure.
6.	Pull images from DockerHub (the public repository of Docker).
7.	Set up ownCloud self-hosted file sync and share server.
8.	Set Up MySQl Database.
9.	Linked both the conatiners
10.	Launching containers with Docker_compose via command: docker -compose up


<b>Requirements/Installation:-</b>

Make sure you have the latest versions of Docker and Docker Compose installed on your machine. If not then follow the below commands_

•	sudo apt-get update</br>
•	sudo apt-get remove docker docker-en</br>
•	gine docker.io</br>
•	sudo apt install docker.io</br>


<b>Docker Installation on RedHat:-</b>

Configure yum by adding docker.repo and dvd.repo inside the “/etc/yum.repos.d” for local installation using the below link: https://download.docker.com/linux/redhat/docker-ce.repo  


<b>Start Docker:-</b>

•	sudo systemctl start docker</br>
•	sudo systemctl enable docker


<b>Install Docker Compose:-</b>

•	sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose</br>
•	sudo chmod +x /usr/local/bin/docker-compose


<b>Download the Required Images:-</b>

Downloading the required docker image for ownCloud and MySQL  from https://hub.docker.com using below commands:

•	docker pull owncloud:latest</br>
•	docker pull mysql: 5.7

  
<b>Using Docker Compose:-</b>

Starting containers:</br>
•	docker-compose start

Stopping containers:-</br>
•	docker-compose stop


<b>Volumes:-</b> 

Persistent Storage: All our data will be permanent if we attach a persistent volume to the containers where OwnCloud and MySQL deployed and stores data. This ensures the data will remain permanent if any of the container crashes or terminates. 
OwnCloud uses database server. So, defining database container and the Database (MySQL in my project) connected as back-end for ownCloud to host on web-server.

docker -d -i -t -e OWN_DB_HOST=(my_database_name) OWN_ROOT_PASSWORD=(your_password) -e OWN_ROOT_USER=(username) -e OWN_PASSWORD=(your_password) -e OWN_DATABASE= (any_database_name) -v name -p 8081:80 --name ownos --link dbos owncloud:latest


<b>Usage:-</b>

Open a terminal and cd to the folder in which `docker-compose.yml` is saved and run the below command_

•	docker-compose up

</br>
</br>

<b>Then we can access the ownCloud server website, built under Docker! </b>

