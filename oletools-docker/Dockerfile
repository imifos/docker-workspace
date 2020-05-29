# Philippe Lagadec's OLETOOLS 
# https://github.com/decalage2/oletools
#
# Build the image:
#   docker build -t oletools .
#
# Open shell:
#   docker run --rm -ti -v /myhost_case_files:/data oletools
#
FROM python:slim-buster
MAINTAINER @imifos

RUN mkdir /tools \
 && groupadd -r tools \
 && useradd -d /tools -s /bin/bash -g tools tools \
 && chown -R tools:tools /tools

USER tools
ENV PATH="/tools/.local/bin:/tools:${PATH}"
RUN pip3 install -U https://github.com/decalage2/oletools/archive/master.zip
WORKDIR /tools
ENTRYPOINT [ "/bin/bash" ]