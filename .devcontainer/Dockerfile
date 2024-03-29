# syntax=docker/dockerfile:1.4
FROM ubuntu:22.04
LABEL org.opencontainers.image.authors="Santoso Wijaya <code@swijaya.com>"

ARG DEBIAN_FRONTEND=noninteractive

RUN <<EOF
  apt update -q
  apt install -qy --no-install-recommends \
    build-essential \
    ca-certificates \
    curl \
    fonts-powerline \
    git \
    gnupg2 \
    libmagickcore-dev \
    nodejs \
    npm \
    procps \
    vim \
    wget \
    xz-utils \
    zlib1g-dev
EOF

# Clean up
RUN apt clean

# Install n (npm version manager); and then install LTS version
RUN <<EOF
  node --version
  npm install -g n
  n lts
EOF
RUN <<EOF
  node --version
  npm --version
EOF

# Use the bash shell with -l (login) from here on.
# The login behavior is important to trigger RVM's setup scripts.
SHELL [ "/bin/bash", "-l", "-c" ]

# Fetch and install RVM, then use it to install Ruby 3.2.3
RUN <<EOF
  gpg2 --keyserver hkp://keys.gnupg.net --recv-keys D39DC0E3
  curl -sSL https://get.rvm.io | bash -s
  . /etc/profile.d/rvm.sh && rvm install 3.2.3
EOF

RUN <<EOF
  rvm list
  ruby -v
  gem install bundler
EOF

# If invoking Jekyll commands that touch files, mount them here.
VOLUME /vol
WORKDIR /vol

ENTRYPOINT ["/bin/bash", "-l", "-c"]
