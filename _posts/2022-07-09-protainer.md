---
title: Portainer your container manager
date: 2022-07-09 11:00:00 +0100
categories: [docker, docker-compose]
tags: [managment, monitoring]     # TAG names should always be lowercase
image:
  path: /assets/img/portainer/portainer_title_image.png
  width: 800
  height: 500
  alt: Portainer your container manager.
---

Portainer Community Edition is a lightweight service delivery platform for containerized applications that can be used to manage Docker, Swarm, Kubernetes and ACI environments. It is designed to be as simple to deploy as it is to use. The application allows you to manage all your orchestrator resources (containers, images, volumes, networks and more) through a ‘smart’ GUI and/or an extensive API.
Portainer consists of a single container that can run on any cluster. It can be deployed as a Linux container or a Windows native container.

## **Depemdemcies**

For everything to work out you will need to make sure that you have the following requirements:

* [docker](https://docs.docker.com/get-docker/)
* [docker-compose](https://docs.docker.com/compose/install/compose-plugin/)

If this is the case we can carrie on creating the pi-hole service.


> It is recomended to clone the GitHub repo [home-lab](https://github.com/r3dspace/home-lab) for the most up to date configuration of this service. 
{: .prompt-info }

## **Setting up portainer container**

Create a `docker-compose.yml` and copy the data below into it. 

```yml
version: '3.9'

volumes:
  data: {}

services:
  portainer:
    image: portainer/portainer-ce:latest    # Image for community edition
    # image: portainer/portainer-ee:latest  # Image for enterprise
    container_name: portianer
    restart: unless-stopped
    volumes:
      - data:/data
      - /etc/localtime:/etc/localtime:ro
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - 9443:9443/tcp
      - 8000:8000/tcp
      - 8000:8000/udp
    # environment:
      # - EDGE_INSECURE_POLL: 1     # Needed when using self signed cert with edge agent
```

## **Managing the portainer container**

All commands listet here should be run in the same directory as the compose file. 

<b>Start</b> the container:

```bash
sudo docker compose up -d
```

<b>Stop</b> the container:

```bash
sudo docker compose stop
```

<b>Restart / rebuild</b> container:

```bash
sudo docker compose up -d --force-recreate
```

<b>Logs</b> view:

```bash
sudo docker compose logs portainer
```

## **Post-install**

After you have startet Portainer visit the url `https://<host-ip-address>:9443`. Here you will need to setup your Portainer instance.

1. Create an default user with administrator rights. It is recomendet to not create a user called root, admin or administrator but something close. 

![setup initial user](/assets/img/portainer/portainer-initial-user-setup.png){: .shadow w="500" h="200" }


## **Edge agent**

Find out more about the use of the edge agent [here](https://downloads.portainer.io/edge_agent_guide.pdf).

<br>

## **Links**

⚙️ If you see something that needs to be fixed, this documentation is open source! Feel free to open an issue [here](https://github.com/r3dspace/r3dspace.github.io).

⭐ If you enjoied the post I would appreciate a star on [GitHub](https://github.com/r3dspace)