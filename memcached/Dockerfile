############################################################
# Dockerfile to build memcached images
############################################################

FROM phusion/baseimage:0.9.15

MAINTAINER Wenbin Fang <wenbin@cs.wisc.edu>

RUN /usr/sbin/enable_insecure_key

ENV HOME /root
RUN /etc/my_init.d/00_regen_ssh_host_keys.sh
CMD ["/sbin/my_init"]

RUN apt-get -qq update

# Install and configure memcached.
RUN apt-get -qq install memcached
RUN sed -i -e 's/^-l 127.0.0.1/-l 0.0.0.0/' /etc/memcached.conf
RUN sed -i -e 's/-u memcache/-u root/' /etc/memcached.conf
ADD run /etc/service/memcached/
RUN chmod 755 /etc/service/memcached/run
EXPOSE 11211

# Clean up.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
