# Dockerfile for installing and running Nginx

From ubuntu:14.04

MAINTAINER Jerry "xiuce123@126.com"

# == Ubuntu Mirror on 163 for China network
RUN \
    echo "deb http://mirrors.163.com/ubuntu/ trusty main restricted universe multiverse" > /etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/ubuntu/ trusty-security main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/ubuntu/ trusty-proposed main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/ubuntu/ trusty-backports main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/ubuntu/ trusty main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/ubuntu/ trusty-security main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/ubuntu/ trusty-proposed main restricted universe multiverse" >> /etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/ubuntu/ trusty-backports main restricted universe multiverse" >> /etc/apt/sources.list

# Install nginx
RUN apt-get update && apt-get install -qy curl

RUN apt-get install -y nginx
RUN apt-get install -y git libmysqlclient-dev nodejs
# RUN apt-get install -y nodejs

RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# RUN apt-get install -y nodejs nodejs-legacy
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash \
        && echo 'registry=https://registry.npm.taobao.org' > /root/.npmrc \
        && source /root/.npmrc \
        && . $NVM_DIR/nvm.sh \
    && nvm install stable

# RUN echo "daemon off;" >> /etc/nginx/nginx.conf
# ADD ../config/nginx-app.conf /etc/nginx/sites-enabled/default

# Install rvm, ruby, bundler
RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
RUN curl -sSL https://get.rvm.io | bash -s stable
RUN /bin/bash -l -c "source /etc/profile.d/rvm.sh"
RUN /bin/bash -l -c "rvm requirements"
RUN /bin/bash -l -c "rvm install 2.3.3"
RUN /bin/bash -l -c "gem install bundler --no-ri --no-rdoc"

# Publish port 80
# EXPOSE 80
