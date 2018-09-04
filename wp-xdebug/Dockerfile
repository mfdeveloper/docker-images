# See: https://stackoverflow.com/questions/46825502/how-do-i-install-xdebug-on-dockers-official-php-fpm-alpine-image#46831699

ARG WORDPRESS_VERSION=latest
FROM "wordpress:$WORDPRESS_VERSION"
ARG WORDPRESS_VERSION
LABEL maintainer="Michel Felipe<mfelipeof@gmail.com>" \
	  description="A wordpress image with xdebug without requirement of XDEBUG_CONFIG" \
	  version="1.0-php7.2-apache"

ENV XDEBUG_PORT 9000
ENV XDEBUG_VERSION 2.6.0
ENV XDEBUG_IDEKEY docker

RUN pecl install "xdebug-${XDEBUG_VERSION}" \
    && docker-php-ext-enable xdebug

RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini && \
	echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/conf.d/xdebug.ini && \
	echo "xdebug.idekey=${XDEBUG_IDEKEY}" >> /usr/local/etc/php/conf.d/xdebug.ini