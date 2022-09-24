---
title: Wireguard a fast & lightweight VPN
date: 2022-09-24 10:00:00 +0100
categories: [docker, compose]
tags: [vpn, security, managment]     # TAG names should always be lowercase
image:
  path: /assets/img/wireguard/wireguard_title_image.png
  width: 800
  height: 500
  alt: Wireguard a fast & lightweight VPN.
---

WireGuard is an extremely simple yet fast and modern VPN that utilizes state-of-the-art cryptography. It aims to be faster, simpler, leaner, and more useful than IPsec, while avoiding the massive headache. It intends to be considerably more performant than OpenVPN. WireGuard is designed as a general purpose VPN for running on embedded interfaces and super computers alike, fit for many different circumstances.


## **Depemdemcies**

For everything to work out you will need to make sure that you have the following requirements:

* [docker](https://docs.docker.com/get-docker/)
* [docker-compose](https://docs.docker.com/compose/install/compose-plugin/)

If this is the case, we can carry on creating the compose stack.

> It is recomended to clone the GitHub repo [home-lab](https://github.com/r3dspace/home-lab) for the most up to date configuration of this service. 
{: .prompt-info }


## **Setting up wireguard network & compose stack**

Use a predefined docker network if you would like to make other containers accessable throught the VPN tunnel. An example usecase would be a mgmt network, where you can access webinterfaces (e.g. Portainer), without exposing the mgmt interface to the web. This will increase your security, by decreases your attack surface from the web.

If you just want WG server for your clients to connect to, you can skip this step. If you do want to add other containers to the WG server you will need to create a docker network called `wireguard_network`.

```bash
sudo docker network create \
    --driver=bridge \
    --subnet=172.155.0.0/16 \
    --ip-range=172.155.5.0/24 \
    --gateway=172.155.5.254 \
    wireguard_network
```

Create a directory for your `docker-compose.yml` file and copy the data below into that file. 

> If you have chosen to make other containers accessible through the VPN tunnel, you will need to enable the networks variables!
{: .prompt-info }

```yml
version: '3.9'

# Enable external network when connecting other containers
# ---
# networks:
  # wg:
    # external:
      # name: wireguard_network

services:
  wireguard:
    image: lscr.io/linuxserver/wireguard:latest
    container_name: wireguard
    restart: always
    cap_add:
      - NET_ADMIN
      - SYS_MODULE
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Berlin
      # Seting server in the client config. 'auto' uses the host
      # ---
      - SERVERURL=auto
      - SERVERPORT=51820
      # Set WG configs for c2s
      # ---
      - PEERS=user1,user2,site1 
      # Set dns provider for clients. 'auto' uses the host
      # ---
      - PEERDNS=auto
      - INTERNAL_SUBNET=10.13.13.0 
      # Allowed IPs for clients. Calculator tool: https://bit.ly/3xOZP1b
      # ---
      - ALLOWEDIPS=0.0.0.0/0
      # Creates QR-config-code
      # ---
      - LOG_CONFS=true   
    volumes:
      - /opt/docker/volumes/wireguard/config:/config
      - /lib/modules:/lib/modules
    ports:
      - 51820:51820/udp
    sysctls:
      - net.ipv4.conf.all.src_valid_mark=1
    # Enable external network when connecting other containers
    # ---
    # networks:
      # wg:
        # Enable when you want to set a custom container IP. Make sure IP matches your created network circles IP!
        # ipv4_address: 172.155.5.250
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


## **Print QR code in CLI**

You can use a [script](https://github.com/r3dspace/home-lab/blob/main/scripts/show-wireguard-qr-in-cli.sh) I have created to print the QR code, or run the following command with your relevant values for *CONTAINER_NAME* and *PEER_NAME*.

```bash
# Add your relevant values for CONTAINER_NAME and PEER_NAME
# ---
sudo docker exec -it CONTAINER_NAME /app/show-peer PEER_NAME
```


## **Linux client**

If you want to connect your linux client to your freshly created WG server, you will first of all need to install it. Run the installation command for your distro.

**Debian / Ubuntu**
```bash
sudo apt install wireguard resolvconf
```

**Fedora**
```bash
sudo dnf install wireguard-tools
```

**Arch**
```bash
sudo pacman -S wireguard-tools
```

### **Setup WG client**

Import your WG peer config into the directory `/etc/wireguard/`. You can import your peer config by running the following command with your information.

```bash
# Replace USERNAME, HOST, PEER_PATH and PEER_NAME with your information
# ---
scp USERNMAE@HOST:PEER_PATH/PEER_NAME.conf /etc/wireguard
```

After you have successfully importet your peer config file, you can now use your WG client. Here are the following commands to manage your wireguard client.

```bash
# Start the VPN tunnel
# ---
sudo wg-quick up PEER_NAME

# Stop the VPN tunnel
# ---
sudo wg-quick down PEER_NAME

# Inspect WG
# ---
sudo wg
```


## **Windows, Mac, Android & iOS clients**

The download link to your relevant system can be found [here](https://www.wireguard.com/install/).
To import your peer config on your phone just scan the QR code in the WG app. To import your peer config on your OS (Windows and Mac) open a terminal and run the following command with your values.

```bash
# Replace USERNAME, HOST, PEER_PATH, PEER_NAME and CLIENT_DOWNLOAD_PATH
# with your information
# ---
scp USERNMAE@HOST:PEER_PATH/PEER_NAME.conf CLIENT_DOWNLOAD_PATH
```


<br>

## **Links**

⚙️ If you see something that needs to be fixed, this documentation is open source! Feel free to open an issue [here](https://github.com/r3dspace/r3dspace.github.io).

⭐ If you enjoied the post I would appreciate a star on [GitHub](https://github.com/r3dspace)