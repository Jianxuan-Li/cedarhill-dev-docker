# Docker file for Python GIS development
# Do not use this image in production
FROM ubuntu:24.04

# Set timezone
ENV TZ America/Toronto
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Set LANG
ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8
ENV LANGUAGE en_US:en

RUN apt-get update -y && apt-get install -y \ 
    wget python3 python3-pip python3-venv \
    # For postgis and Django gis
    gdal-bin python3-gdal libgdal-dev \
    # For weasyprint
    libpango-1.0-0 libharfbuzz0b libpangoft2-1.0-0 libharfbuzz-subset0 libffi-dev libjpeg-dev libopenjp2-7-dev \
    # Other utils
    gettext iputils-ping telnet net-tools vim curl zsh git \
    && apt-get autoremove -y && apt-get autoclean -y && rm -rf /var/lib/apt/lists/*

# Install pypoetry
RUN curl -sSL https://install.python-poetry.org | POETRY_VERSION=1.8.4 python3 -
ENV PATH="/root/.local/bin:$PATH"

# install oh-my-zsh
RUN wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O - | zsh || true

# zsh plugin for poetry
RUN mkdir /root/.oh-my-zsh/custom/plugins/poetry \
    && poetry completions zsh > /root/.oh-my-zsh/custom/plugins/poetry/_poetry \
    && sed -i 's/plugins=(git)/plugins=(git poetry)/g' /root/.zshrc

# Project initalization
RUN mkdir /code
VOLUME  ["/code"]
WORKDIR /code
EXPOSE 8000

CMD ["zsh"]
