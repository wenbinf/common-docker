Common Dockerfiles
==================

Some reusable Dockerfiles for my projects.

All these docker images are based on phusion/baseimage. So we can easily ssh into any container.

SSH into it (Replace $NAME with the container's name):

    curl -o ~/.ssh/insecure_key -fSL https://github.com/phusion/baseimage-docker/raw/master/image/insecure_key
    chmod 600 ~/.ssh/insecure_key
    ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" $NAME)

You can add an alias to ~/.bashrc, e.g.,

    alias ssh-devbox="ssh -i ~/.ssh/insecure_key root@$(docker inspect -f "{{ .NetworkSettings.IPAddress }}" $NAME)"
