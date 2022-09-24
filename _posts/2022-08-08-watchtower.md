---
title: Watchtower watching for container updates
date: 2022-08-08 14:00:00 +0200
categories: [docker, compose]
tags: [update, security]     # TAG names should always be lowercase
image:
  path: /assets/img/watchtower/watchtower_title_image.png
  width: 800
  height: 500
  alt: Watchtower watching for container updates.
---

With watchtower you can update the running version of your containerized app simply by pushing a new image to the Docker Hub or your own image registry. Watchtower will pull down your new image, gracefully shut down your existing container and restart it with the same options that were used when it was deployed initially.


## **Depemdemcies**

For everything to work out you will need to make sure that you have the following requirements:

* [docker](https://docs.docker.com/get-docker/)
* [docker-compose](https://docs.docker.com/compose/install/compose-plugin/)

If this is the case, we can carry on creating the pi-hole service.


> It is recomended to clone the GitHub repo [home-lab](https://github.com/r3dspace/home-lab) for the most up to date configuration of this service. 
{: .prompt-info }


## **Setting up portainer container**

Create a `docker-compose.yml` and copy the data below into it. 

```yml
version: '3.9'

services:
  watchtower:
    image: containrrr/watchtower
    container_name: watchtower
    restart: unless-stopped
    volumes: 
      - /var/run/docker.sock:/var/run/docker.sock
      - /etc/localtime:/etc/localtime:ro
    command:
      --schedule "0 5 * * * *"
      --rolling-restart
      --cleanup
      # --debug         # Use for debugging
```


## **Commen arguments**

Here are some other usefull arguments that can be used to manage the Watchtower instance. For more arguments visit the [Watchtower website](https://containrrr.dev/watchtower/arguments/).

### **Scheduling**

[Cron expression](https://pkg.go.dev/github.com/robfig/cron@v1.2.0#hdr-CRON_Expression_Format) in 6 fields (rather than the traditional 5) which defines when and how often to check for new images. Either `--interval` or the schedule expression can be defined, but not both. An example: `--schedule "0 0 4 * * *"`.

```
            Argument: --schedule, -s
Environment Variable: WATCHTOWER_SCHEDULE
                Type: String
             Default: -

```

### **Rolling restart**

Restart one image at time instead of stopping and starting all at once. Useful in conjunction with lifecycle hooks to implement zero-downtime deploy.

```
            Argument: --rolling-restart
Environment Variable: WATCHTOWER_ROLLING_RESTART
                Type: Boolean
             Default: false

```

### **Revive stopped**

Start any stopped containers that have had their image updated. This argument is only usable with the `--include-stopped` argument.
```
            Argument: --revive-stopped
Environment Variable: WATCHTOWER_REVIVE_STOPPED
                Type: Boolean
             Default: false
```

### **Cleanup**

Removes old images after updating. When this flag is specified, watchtower will remove the old image after restarting a container with a new image. Use this option to prevent the accumulation of orphaned images on your system as containers are updated.

```
            Argument: --cleanup
Environment Variable: WATCHTOWER_CLEANUP
                Type: Boolean
             Default: false

```

### **Filter by enable label**

Update containers that have a `com.centurylinklabs.watchtower.enable` label set to true.
```
            Argument: --label-enable
Environment Variable: WATCHTOWER_LABEL_ENABLE
                Type: Boolean
             Default: false
```

### **Wait until timeout**

Timeout before the container is forcefully stopped. When set, this option will change the default (10s) wait time to the given value. An example: `--stop-timeout 30s` will set the timeout to 30 seconds.
```
            Argument: --stop-timeout
Environment Variable: WATCHTOWER_TIMEOUT
                Type: Duration
             Default: 10s
```

### **Filter by disable label**

Do not update containers that have `com.centurylinklabs.watchtower.enable` label set to false and no `--label-enable` argument is passed. Note that only one or the other (targeting by enable label) can be used at the same time to target containers.

### **Wait until timeout**

Timeout before the container is forcefully stopped. When set, this option will change the default (10s) wait time to the given value. An example: `--stop-timeout 30s` will set the timeout to 30 seconds.

```
            Argument: --stop-timeout
Environment Variable: WATCHTOWER_TIMEOUT
                Type: Duration
             Default: 10s

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

<br>

## **Links**

⚙️ If you see something that needs to be fixed, this documentation is open source! Feel free to open an issue [here](https://github.com/r3dspace/r3dspace.github.io).

⭐ If you enjoied the post I would appreciate a star on [GitHub](https://github.com/r3dspace)