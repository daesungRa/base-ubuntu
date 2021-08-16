FROM ubuntu:20.04
MAINTAINER Ra Daesung "daesungra@gmail.com"

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8 TZ=Asia/Seoul
ARG PYTHON_VERSION=3.9.6

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

### Mandatory packages for system && pyenv ###
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
        systemd vim curl git wget make llvm sudo \
        build-essential \
        libbz2-dev \
        libncurses5-dev \
        libncursesw5-dev \
        libreadline-dev \
        libsqlite3-dev \
        libssl-dev \
        tk-dev \
        xz-utils \
        zlib1g-dev \
        libffi-dev \
        liblzma-dev \
        python-openssl

# Install pyenv
RUN curl https://pyenv.run | bash

# Pyenv config
ENV HOME=/root
ENV PYTHON_ROOT=/root/.pyenv
ENV PATH="$HOME/.pyenv/shims:$HOME/.pyenv/bin:$PATH"

# Init pyenv
RUN eval "$(pyenv init -)"
RUN eval "$(pyenv virtualenv-init -)"

# Set global python & pip
RUN pyenv install $PYTHON_VERSION && pyenv global $PYTHON_VERSION
RUN pip install --upgrade pip
RUN pip install virtualenv
RUN pip install --upgrade virtualenv

# base working directory
RUN mkdir /serve
WORKDIR /serve

