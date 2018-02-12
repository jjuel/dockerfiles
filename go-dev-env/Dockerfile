FROM golang:alpine

MAINTAINER Jordan Juel (http://github.com/jjuel)

RUN apk update && \
    apk add --no-cache git \
    	    	       zsh \
		       curl
		       

ENV SHELL /bin/zsh

RUN git clone --depth 1 https://github.com/robbyrussell/oh-my-zsh.git /root/.oh-my-zsh \
    && echo 'export ZSH=/root/.oh-my-zsh' >> /root/.zshrc \
    && echo 'ZSH_THEME="jordanjuel"' >> /root/.zshrc \
    && echo 'plugins=(git docker)' >> /root/.zshrc \
    && echo 'source $ZSH/oh-my-zsh.sh' >> /root/.zshrc \
    && echo 'export TERM=xterm-256color' >> /root/.zshrc 

# RUN go get -u github.com/golang/dep/cmd/dep

COPY ./.oh-my-zsh /root/.oh-my-zsh/

cmd ["/bin/zsh"]