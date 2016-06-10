FROM debian:jessie

RUN echo "deb http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu wily main" >> /etc/apt/sources.list \
    && echo "deb-src http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu wily main" >> /etc/apt/sources.list \
    && apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 9DBB0BE9366964F134855E2255F96FCF8231B6DD \
    && apt-get update \
    && apt-get -y upgrade \
    && apt-get -y install neovim --no-install-recommends

ENTRYPOINT ["nvim"]
