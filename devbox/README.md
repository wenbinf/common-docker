docker-devbox
=============

Docker Memcached Image

In docker hub:
    https://registry.hub.docker.com/u/wenbinf/devbox/

Run it:

    # It'll map ~/src on local host to /root/src in the devbox container.
    # So you can put your source code inside ~/src.
    docker run -d --name devbox -v ~/src:/root/src -p 22 wenbinf/devbox

