# Cyberchef
#
# Builds the latest version from source and starts a local server. 
#
# Note:
#  Using UBUNTU as base image as I also use the below in combo-containers.
#
# Version:
#  0.1  08/05/2020
#
# Build the image:
#   docker build -t cyberchef .
#
# Use Cases:
#   Base:
#      docker run --rm -p 6401:8080 cyberchef 
#      http://localhost:6401/
#      Exit: Ctrl+C in container window
#
FROM ubuntu:focal-20200423
MAINTAINER @imifos

ENV NODE_OPTIONS=--max_old_space_size=2048
ENV DEBIAN_FRONTEND=noninteractive

RUN groupadd -r tools \
 && useradd -d /tools -s /bin/bash -g tools tools

RUN apt-get update \
 && apt-get dist-upgrade -y \
 && apt-get install --no-install-recommends -y git curl  \
 && mkdir /tools && cd /tools \
 && curl -sL https://deb.nodesource.com/setup_10.x | bash - \
 && apt-get install -y --no-install-recommends nodejs npm jq unzip \
 && npm install -g grunt-cli \
 && npm install -g http-server \
 && git clone -v --progress https://github.com/gchq/CyberChef.git \
 && cd CyberChef \
 && sed -i -e 's/Download\ CyberChef/CyberChef\ in\ Local\ Docker/g' src/web/html/index.html \
 && sed -i -e 's/file\_download/home/g' src/web/html/index.html \
 && sed -i -e 's/CyberChef_v/Version:/g' src/web/html/index.html \
 && sed -i -e 's/\.zip/ /g' src/web/html/index.html \
 && npm install \
 && npm audit fix \
 && grunt prod \
 && chown -R tools:tools /tools/CyberChef/build/prod \
 && cd /tools/CyberChef && rm -rf tests && rm -rf src && rm -rf node_modules && rm *.* \
 && apt remove -y git curl \
 && apt autoremove -y \
 && rm -rf /var/lib/apt/lists/* 

USER tools
EXPOSE 8080
WORKDIR /tools/CyberChef/build/prod

CMD [ "http-server","-p","8080" ]