# AccessData FTK Imager v3.1.1 CLI (Aug 24 2012) in Docker
#
# Build the image:
#   Download the ftkimager tar.gz file into Dockerfile directory
#   (Source: https://accessdata.com/product-download/debian-and-ubuntu-x64-3-1-1)
#   
#   docker build -t ftkimager .
#
# Use Cases:
#   Test and Help:
#      docker run --rm 
#
#   Convert RAW to EWF/E01
#      Input and output files must be in current directory
#      docker run -ti --rm -v `pwd`:`pwd` -w `pwd` 5b1 inimage.raw outimage --e01 --compress 9
#
FROM ubuntu:focal-20200423
MAINTAINER @imifos

RUN mkdir /tools \
 && groupadd -r tools \
 && useradd -d /tools -s /bin/bash -g tools tools

COPY ftkimager.3.1.1_ubuntu64.tar.gz /tools

RUN cd /tools \
 && tar -xf ftkimager.3.1.1_ubuntu64.tar.gz \
 && rm ftkimager.3.1.1_ubuntu64.tar.gz \
 && chown tools:tools /tools/ftkimager

USER tools

WORKDIR /tools

ENTRYPOINT [ "/tools/ftkimager" ]