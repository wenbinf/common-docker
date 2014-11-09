Dev Box Docker Image
====================

It contains some dev tools that I use for my projects.

In docker hub:
    https://registry.hub.docker.com/u/wenbinf/devbox/

Run it:

    # Optional command line arguments:
    #   -v ~/src:/root/src It'll map ~/src on local host to /root/src in the container.
    #                      So you can put your source code inside ~/src.
    #   --link memcached:memcached It'll link memcached container to this devbox container.
    #                              See /etc/hosts inside devbox container for hostname/ip.
    docker run -d --name devbox -v ~/src:/root/src -p 22 wenbinf/devbox

SSH into it:

    curl -o ~/.ssh/insecure_key -fSL https://github.com/phusion/baseimage-docker/raw/master/image/insecure_key
    chmod 600 ~/.ssh/insecure_key
    ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" devbox)

You can add an alias to ~/.bashrc, e.g.,

    alias ssh-devbox="ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" devbox)"
