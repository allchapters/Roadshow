FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive

# make /bin/sh symlink to bash instead of dash:
RUN echo "dash dash/sh boolean false" | debconf-set-selections
RUN dpkg-reconfigure dash

# install Cisco fonts
COPY ./docker/cl-labs/fonts/* /usr/share/fonts/truetype/

RUN apt-get -y update \
    && apt-get -y install python3-pip python3-cffi python3-brotli libpango-1.0-0 libharfbuzz0b libpangoft2-1.0-0 git rsync wget unzip curl jq

COPY ./requirements.txt ./
RUN pip install --upgrade pip setuptools pre-commit \
    && pip install -r requirements.txt
