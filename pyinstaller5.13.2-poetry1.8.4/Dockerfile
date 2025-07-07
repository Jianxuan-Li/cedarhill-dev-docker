# Docker file for Python and PyGDAL deployment
FROM ubuntu:24.04

# Set timezone
ENV TZ Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Set LANG
ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8
ENV LANGUAGE en_US:en

RUN apt-get update -y && apt-get install -y \ 
    python3 python3-gdal python3-pip curl \
    # For weasyprint
    libpango-1.0-0 libharfbuzz0b libpangoft2-1.0-0 libharfbuzz-subset0 libffi-dev libjpeg-dev libopenjp2-7-dev \
    && pip3 install --no-cache-dir --break-system-packages pyinstaller==5.13.2 \
    && curl -sSL https://install.python-poetry.org | POETRY_VERSION=1.8.4 python3 - \
    && apt-get remove -y curl \
    && apt-get autoremove -y && apt-get autoclean -y && rm -rf /var/lib/apt/lists/*

ENV PATH="/root/.local/bin:$PATH"
