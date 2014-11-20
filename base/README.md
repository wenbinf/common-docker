Docker Base Image
====================

The base image for all of my docker images.

In docker hub:
    https://registry.hub.docker.com/u/wenbinf/base/

Run it:

    docker run -d --name base -p 22 wenbinf/base

SSH into it:

    curl -o ~/.ssh/insecure_key -fSL https://github.com/phusion/baseimage-docker/raw/master/image/insecure_key
    chmod 600 ~/.ssh/insecure_key
    ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" base)

You can add an alias to ~/.bashrc, e.g.,

    alias ssh-devbox="ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" base)"

Use it in Dockerfile of other images:

    FROM wenbinf/base

    # If you want to run some commands, then in same directory,
    # put a bash script file, called run
    ADD run /root/
    RUN chmod 755 /root/run

The run bash script looks like this:

    #!/bin/bash

    /sbin/my_init -- /usr/sbin/nginx -c /etc/nginx/nginx.conf -g "daemon off;"
    
