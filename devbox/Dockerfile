############################################################
# Dockerfile to build devbox images
############################################################

FROM wenbinf/base

MAINTAINER Wenbin Fang <wenbin@cs.wisc.edu>

# Install some development tools

RUN apt-get -qq update
RUN apt-get -qq install emacs tmux python gcc g++ git wget unzip python-pip

# Install dotfiles
ADD conf/tmux.conf /root/.tmux.conf
RUN cd /tmp && wget https://github.com/wenbinf/emacs.d/archive/master.zip && unzip master.zip && rm -rf /root/.emacs.d && mv /tmp/emacs.d-master /root/.emacs.d

# Clean up.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
