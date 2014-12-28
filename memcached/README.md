Memcached Docker Image
======================

It provides memcached service.

In docker hub:
    https://registry.hub.docker.com/u/wenbinf/memcached/

Run it:

    docker run -d --name memcached -p 22 -p 11211:11211 wenbinf/memcached

## Two ways to log into the container

### Via docker exec

Run this (need docker > 1.3):

    docker exec -it memcached /bin/bash

You can add this shortcut to ~/.bashrc, e.g.,

    ssh_devbox() {
        docker exec -it memcached /bin/bash
    }

So you can use such command to login devbox:
    
    ssh_memcached


### Via SSH

SSH into it:

    curl -o ~/.ssh/insecure_key -fSL https://github.com/phusion/baseimage-docker/raw/master/image/insecure_key
    chmod 600 ~/.ssh/insecure_key
    ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" memcached)

You can add this shortcut to ~/.bashrc, e.g.,

    ssh_memcached() {
        ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" memcached)
    }

So you can use such command to login devbox:
    
    ssh_memcached
