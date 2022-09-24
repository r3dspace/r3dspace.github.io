---
title: Portainer your container manager
date: 2022-07-09 11:00:00 +0100
categories: [docker, compose]
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

If this is the case, we can carry on creating the compose stack.


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
      - /etc/localtime:/etc/localtime:ro
      - /var/run/docker.sock:/var/run/docker.sock
      - data:/data
    ports:
      - 9443:9443/tcp
      - 8000:8000/tcp
    # environment:
      # - EDGE_INSECURE_POLL: 1     # Needed when using self signed cert with edge agent
```

## **Managing the compose stack**

The following commands should be run in the same directory as the docker compose file.

```bash
# Start the compose stack
# ---
sudo docker compose up -d

# Stop the compose stack
# ---
sudo docker compose down

# Rebuild / restart the compose stack
# ---
sudo docker compose up -d --force-recreate

# View the compose stack logs
# ---
sudo docker compose logs portainer
```

## **Post-install**

After you have started Portainer visit the url `https://<host-ip-address>:9443`. Here you will need to setup your admin account for your Portainer instance. Just type in a username, password and optionally opt out of the *annonymouse statistics* collection.

> Try NOT to use a username, like *root*, *admin* or *administrator*, instead use a username such as *aH2gme4*. This will increase your resistance against brut force attacks. Also have a password with at least 12 characters. It should include upper and lowercase letters, numbers and symbols.
{: .prompt-tip }

![setup initial user](/assets/img/portainer/portainer-post-instal-1.png){: .shadow w="800" h="500" }

After successfully login in to your Portainer instance you can click on `Get Started` to start creating containers and stacks on your host. If you want to link another Host with your Portainer instance you can click on `Add Environments`.

![setup initial user](/assets/img/portainer/portainer-post-instal-2.png){: .shadow w="800" h="500" }

Congratulations 🎉 you have successfully set up your Portainer instance.

![setup initial user](/assets/img/portainer/portainer-post-instal-3.png){: .shadow w="800" h="500" }

## **Edge agent**

Find out more about the use of the edge agent [here](https://downloads.portainer.io/edge_agent_guide.pdf).

<br>

## **Links**

⚙️ If you see something that needs to be fixed, this documentation is open source! Feel free to open an issue [here](https://github.com/r3dspace/r3dspace.github.io).

⭐ If you enjoied the post I would appreciate a star on [GitHub](https://github.com/r3dspace)