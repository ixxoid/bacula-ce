FROM ixxoid/bacula-common-ce:11.0.5-1

LABEL maintainer="ixxoid@bluewin.ch"

ENV DEBIAN_FRONTEND=noninteractive

RUN wget -qO - http://www.bacula.org/downloads/baculum/baculum.pub | apt-key add -

COPY files/baculum.list /etc/apt/sources.list.d/baculum.list

RUN apt-get update \
    && apt-get install -y \
		baculum-common \
		baculum-web \
		baculum-web-apache2 \
		php-fpm \
		supervisor

COPY files/sudoers-baculum /etc/sudoers.d/sudoers-baculum 

COPY files/supervisord.conf /etc/supervisor/supervisord.conf

VOLUME ["/opt/bacula/etc","/etc/baculum"]

RUN mkdir -p /run/php

RUN a2enmod rewrite

RUN a2ensite baculum-web

RUN service apache2 restart

RUN apt-get clean

EXPOSE 9095/tcp

ENTRYPOINT ["/usr/bin/supervisord"]