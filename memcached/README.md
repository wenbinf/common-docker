Memcached Docker Image
======================

It provides memcached service.

In docker hub:
    https://registry.hub.docker.com/u/wenbinf/memcached/

Run it:

    docker run -d --name memcached -p 22 -p 11211:11211 wenbinf/memcached

SSH into it:

    curl -o ~/.ssh/insecure_key -fSL https://github.com/phusion/baseimage-docker/raw/master/image/insecure_key
    chmod 600 ~/.ssh/insecure_key
    ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" memcached)

You can add an alias to ~/.bashrc, e.g.,

    alias ssh-devbox="ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" memcached)"
