# syntax=docker/dockerfile:1.4
FROM ubuntu:22.04
LABEL org.opencontainers.image.authors="Santoso Wijaya <code@swijaya.com>"

ARG DEBIAN_FRONTEND=noninteractive

RUN <<EOF
  apt-get update -q
  apt-get install -qy --no-install-recommends \
    procps \
    curl \
    ca-certificates \
    gnupg2 \
    build-essential \
    zlib1g-dev \
    wget \
    xz-utils
EOF

# Clean up
RUN apt-get clean

# Use the bash shell with -l (login) from here on.
# The login behavior is important to trigger RVM's setup scripts.
SHELL [ "/bin/bash", "-l", "-c" ]

# Fetch and install RVM, then use it to install Ruby 3.1.3
RUN <<EOF
  gpg2 --keyserver hkp://keys.gnupg.net --recv-keys D39DC0E3
  curl -sSL https://get.rvm.io | bash -s
  . /etc/profile.d/rvm.sh && rvm install 3.1.3
EOF

RUN <<EOF
  rvm list
  ruby -v
  gem install jekyll bundler
EOF

# If invoking Jekyll commands that touch files, mount them here.
VOLUME /vol
WORKDIR /vol

ENTRYPOINT ["/bin/bash", "-l", "-c"]
