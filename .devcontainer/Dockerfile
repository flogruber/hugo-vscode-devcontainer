FROM alpine:latest

ENV HUGO_VERSION 0.58.3

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN apk add --no-cache \
    bash \
    curl \
    git \
    sudo

RUN addgroup -S $USERNAME --gid $USER_GID \
    && adduser -S $USERNAME --uid $USER_UID -G $USERNAME

RUN echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME\
    && chmod 0440 /etc/sudoers.d/$USERNAME

RUN mkdir -p /usr/local/src \
    && cd /usr/local/src \
    && curl -L https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_${HUGO_VERSION}_linux-64bit.tar.gz | tar -xz \
    && mv hugo /usr/local/bin/hugo 

EXPOSE 1313