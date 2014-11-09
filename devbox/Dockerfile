############################################################
# Dockerfile to build devbox images
############################################################

FROM phusion/baseimage:0.9.15

MAINTAINER Wenbin Fang <wenbin@cs.wisc.edu>

RUN /usr/sbin/enable_insecure_key

ENV HOME /root
RUN /etc/my_init.d/00_regen_ssh_host_keys.sh
CMD ["/sbin/my_init"]

RUN apt-get -qq update

# Install some development tools
RUN apt-get -qq install emacs
RUN apt-get -qq install tmux
RUN apt-get -qq install python
RUN apt-get -qq install gcc
RUN apt-get -qq install g++
RUN apt-get -qq install git
RUN apt-get -qq install wget
RUN apt-get -qq install unzip

# Install dotfiles
ADD conf/tmux.conf /root/.tmux.conf
RUN cd /tmp && wget https://github.com/wenbinf/emacs.d/archive/master.zip && unzip master.zip && rm -rf /root/.emacs.d && mv /tmp/emacs.d-master /root/.emacs.d

# Clean up.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
