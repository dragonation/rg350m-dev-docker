FROM debian:buster-slim as rg350m-dev
LABEL maintainer="minun (dragonation@gmail.com)"

# prepare timezone info
RUN ln -snf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo 'Asia/Shanghai' > /etc/timezone 

# prepare docker environment, using 163 repo in china
ENV DEBIAN_FRONTEND noninteractive
RUN echo 'deb http://mirrors.163.com/debian/ buster main non-free contrib' > /etc/apt/sources.list && \
    echo 'deb http://mirrors.163.com/debian-security/ buster/updates main non-free contrib' >> /etc/apt/sources.list && \
    apt-get update && \
    mkdir -p /usr/share/man/man1 && \
    apt-get install -y \
        automake build-essential ccache cmake patch \
        gcc-multilib g++-multilib \
        python python3 perl openjdk-11-jdk \
        bash bc bison cpio file flex gettext locales man sed texinfo time vim \
        curl wget \
        bzip2 gzip tar unzip zip \
        bzr cvs git mercurial rsync subversion \
        asciidoc w3m dblatex graphviz python-matplotlib \
        dosfstools mtools squashfs-tools \
        libncurses5-dev libc6-dev-i386 libssl-dev

# prepare locale
RUN sed -i 's/# \(en_US.UTF-8\)/\1/' /etc/locale.gen && \
    /usr/sbin/locale-gen
ENV LC_ALL en_US.UTF-8

# prepare prebinding directories and environments
RUN mkdir -p /rg350m && \
    mkdir -p /rg350m/buildroots && \
    mkdir -p /rg350m/commands && \
    mkdir -p /rg350m/transfer && \
    mkdir -p /rg350m/toolchain

# prepare user
RUN useradd -m -s /bin/bash rg350m && \
    chown -R rg350m:rg350m /home/rg350m
USER rg350m
ENV HOME /home/rg350m
ENV PATH /rg350m/commands:$PATH
WORKDIR /rg350m

ENV BR2_JLEVEL 0
