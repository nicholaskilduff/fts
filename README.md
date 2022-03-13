FTS Solution Installation and Troubleshooting Guide

Server Installation

The installation of FreeTAKServer was done on Ubuntu Server 20.04 LTS

**Make sure to create a volume large for the VM, had to increase the size of the drive without interrupting services, used the below link to do so:

https://medium.com/geekculture/tutorial-how-to-extend-aws-ebs-volumes-with-no-downtime-ec7d9e82426e

The following resources were used:
https://medium.com/geekculture/tutorial-how-to-extend-aws-ebs-volumes-with-no-downtime-ec7d9e82426e
https://github.com/joshuafuller/ATAK-Maps
https://freetakteam.github.io/FreeTAKServer-User-Docs/Installation/Docker/

Below are the commands to update the machine after initial creation and the installation of FTS via docker:

sudo apt update -y && sudo apt upgrade -y

sudo apt install docker.io -y

sudo docker volume create fts_data

sudo docker run -d -p 8080:8080/tcp -p 8087:8087/tcp -e FTS_CONNECTION_MESSAGE="Server Connection Message" -e FTS_COT_TO_DB="True" -v fts_data:/data --name fts --restart unless-stopped freetakteam/freetakserver:1.1.2

The following command can be used to open a CLI instance to the FTS server running within the container:

sudo docker exec -it fts python3 -m FreeTAKServer.views.CLI





Client Installation and Configuration
