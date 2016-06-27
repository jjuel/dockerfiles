FROM debian:jessie

RUN apt-get update && apt-get install -y \
	git \
	software-properties-common \
	python-dev \
	python-pip \
	python3-dev \
	python3-pip \
	tmux \
	curl \
	zsh \
	&&  echo "deb http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu wily main" >> /etc/apt/sources.list \
	&& echo "deb-src http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu wily main" >> /etc/apt/sources.list \
    	&& apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 9DBB0BE9366964F134855E2255F96FCF8231B6DD \
	&& apt-get update \
	&& apt-get install -y neovim --no-install-recommends \
	&& rm -rf /var/lib/apt/lists/* \
	&& chsh -s /usr/bin/zsh \
	&& pip install neovim

RUN curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh

ENV GOLANG_VERSION 1.6.2
ENV GOLANG_DOWNLOAD_URL https://golang.org/dl/go$GOLANG_VERSION.linux-amd64.tar.gz
ENV GOLANG_DOWNLOAD_SHA256 e40c36ae71756198478624ed1bb4ce17597b3c19d243f3f0899bb5740d56212a
ENV TERM=xterm-256color

RUN curl -fsSL "$GOLANG_DOWNLOAD_URL" -o golang.tar.gz \
	&& echo "$GOLANG_DOWNLOAD_SHA256  golang.tar.gz" | sha256sum -c - \
	&& tar -C /usr/local -xzf golang.tar.gz \
	&& rm golang.tar.gz

ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH
ENV SHELL /usr/bin/zsh

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH


COPY ./.zshrc /root/.zshrc
COPY ./init.vim /root/.config/nvim/
COPY ./.oh-my-zsh /root/.oh-my-zsh/
COPY ./autoload /root/.config/nvim/autoload

CMD ["/bin/zsh"]