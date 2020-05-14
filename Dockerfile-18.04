# base image
FROM ubuntu:18.04

# maintainer
MAINTAINER Karel Fiala <fiala.karel@gmail.com>

# fix locales and set vars
ENV LANG="en_US.UTF-8" \
    LANGUAGE="en_US:en" \
    TERM="xterm" \
    EDITOR="vim" \
    TZ="Europe/Prague" \
    DEBIAN_FRONTEND="noninteractive" \
    SHELL="/bin/bash" \
    UBUNTU_VERSION="18.04" \
    PATH="/opt/bin:$PATH"

RUN    mkdir -p /opt/bin \
    && chmod -R 777 /opt \
    && echo "Europe/Prague" >/etc/timezone \
    && apt-get update \
    && apt-get install -o Dpkg::Options::="--force-overwrite" --fix-broken --yes \
        dumb-init vim wget \
    && apt-get clean \
    && rm -rf /var/cache/* \
    && rm -rf /var/lib/apt/lists/*

# set entrypoint
ENTRYPOINT ["/usr/bin/dumb-init", "--"]

CMD ["/bin/bash"]
