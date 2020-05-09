# tsschecker in docker
# 
# Pulls and compiles latest versions of source code from original repositories.
# 
# Version:
#  0.1  25/02/2020
#
# Build the image:
#   docker build -t tsschecker .
#
# Run image:
#   docker run --rm tsschecker -h
#   docker run --rm tsschecker --list-ios --device iPad8,3
#   docker run --rm tsschecker --list-devices
#
FROM ubuntu:bionic-20200219
MAINTAINER @imifos

RUN apt-get update \
 && apt-get dist-upgrade -y \
 && apt-get install -y git openssl libssl-dev libreadline-dev libusb-1.0-0-dev libcurl3-dev libzip-dev automake pkg-config build-essential python-dev libtool \
 && rm -rf /var/lib/apt/lists/*

RUN cd /home \
 && git clone https://github.com/libimobiledevice/libirecovery.git \
 && git clone https://github.com/libimobiledevice/libplist.git \
 && git clone https://github.com/tihmstar/tsschecker.git \
 && git clone https://github.com/tihmstar/libgeneral \
 && git clone https://github.com/tihmstar/libfragmentzip.git \
 && cd tsschecker && git submodule update --init --recursive && git pull --recurse-submodules

RUN cd /home \
 && cd libplist && ./autogen.sh && make && make install && cd .. \
 && cd libirecovery && ./autogen.sh && make && make install && cd .. \
 && cd libgeneral && ./autogen.sh && make && make install && cd .. \
 && cd libfragmentzip && ./autogen.sh && make && make install && cd .. \
 && cd tsschecker && ./autogen.sh && make && make install && cd .. 

RUN cd /home \
 && rm -rf libfragmentzip/ libgeneral/ libirecovery/ libplist/ tsschecker/ \
 && apt remove -y automake pkg-config build-essential python-dev libtool \
 && apt autoremove -y

RUN useradd -ms /bin/bash tool
USER tool
WORKDIR /home/tool

ENV LD_LIBRARY_PATH="/usr/local/lib:${LD_LIBRARY_PATH}"

ENTRYPOINT [ "tsschecker" ]
