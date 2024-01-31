# syntax=docker/dockerfile:1.4
FROM ubuntu:22.04
LABEL org.opencontainers.image.authors="Santoso Wijaya <code@swijaya.com>"

RUN <<EOF
  apt-get update
  apt-get install -y \
    ruby-full \
    build-essential \
    zlib1g-dev \
    wget \
    gpg \
    xz-utils
EOF

# Use the bash shell from here on.
SHELL ["/bin/bash", "-ec"]

# Fetch and install ruby-install
RUN <<EOF
  wget https://github.com/postmodern/ruby-install/releases/download/v0.9.3/ruby-install-0.9.3.tar.gz
  tar -xzvf ruby-install-0.9.3.tar.gz
  pushd ruby-install-0.9.3
  make install
  popd
EOF

RUN <<EOF
  ruby-install -V
  ruby-install ruby 3.1.3
EOF

# Fetch and install chruby
RUN <<EOF
  wget https://github.com/postmodern/chruby/releases/download/v0.3.9/chruby-0.3.9.tar.gz
  tar -xzvf chruby-0.3.9.tar.gz
  pushd chruby-0.3.9
  make install
  popd
EOF

# Image cleanup
RUN <<EOF
  apt-get clean
  rm -rf ruby-install-0.9.3 ruby-install-0.9.3.tar.gz
  rm -rf chruby-0.3.9 chruby-0.3.9.tar.gz
EOF

COPY <<EOF /etc/profile.d/chruby.sh
[ -n "$BASH_VERSION" ] || [ -n "$ZSH_VERSION" ] || return
source /usr/local/share/chruby/chruby.sh
source /usr/local/share/chruby/auto.sh
chruby ruby-3.1.3
EOF

# Something wrong here! When I execute `docker run ... bash` I still don't see 
# chruby activate!
RUN <<EOF
  echo >> ~/.profile
  echo 'source /usr/local/share/chruby/chruby.sh' >> ~/.profile
  echo 'source /usr/local/share/chruby/auto.sh' >> ~/.profile
  echo 'chruby ruby-3.1.3' >> ~/.profile
EOF

RUN <<EOF
  exec /bin/bash
  chruby
  ruby -v
  gem install jekyll bundler
EOF

CMD ["irb"]
