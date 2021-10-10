FROM ixxoid/bacula-common-ce:11.0.5

ENV DEBIAN_FRONTEND=noninteractive

RUN wget -qO - http://www.bacula.org/downloads/baculum/baculum.pub | apt-key add -

COPY files/baculum.list /etc/apt/sources.list.d/baculum.list

RUN apt-get update \
    && apt-get install -y \
		baculum-common \
		baculum-api \
		baculum-api-apache2 \
		php-fpm \
		sudo \
		supervisor

COPY files/sudoers-baculum /etc/sudoers.d/sudoers-baculum 

COPY files/supervisord.conf /etc/supervisor/supervisord.conf

COPY files/api.conf /usr/share/baculum/htdocs/protected/API/Config/api.conf

RUN chown -R www-data:www-data /etc/baculum/

RUN mkdir -p /run/php

RUN a2enmod rewrite

RUN a2ensite baculum-api

RUN apt-get clean

EXPOSE 9096/tcp

ENTRYPOINT ["/usr/bin/supervisord"]