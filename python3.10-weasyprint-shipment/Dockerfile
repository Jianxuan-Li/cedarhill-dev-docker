# Docker file for Python and PyGDAL deployment
FROM ubuntu:22.04

# Set timezone
ENV TZ Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Set LANG
ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8
ENV LANGUAGE en_US:en

RUN apt-get update -y && apt-get install -y \ 
    python3 python3-gdal python3-pip \
    python3-cffi python3-brotli libpango-1.0-0 libharfbuzz0b libpangoft2-1.0-0 \
    && apt-get autoremove -y && apt-get autoclean -y && rm -rf /var/lib/apt/lists/*
