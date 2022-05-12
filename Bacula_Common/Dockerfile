FROM debian:bullseye

LABEL maintainer="ixxoid@bluewin.ch"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y \
		apt-utils \
		apt-transport-https \
		gnupg \
		ca-certificates \
		wget

RUN cd /tmp
RUN wget https://www.bacula.org/downloads/Bacula-4096-Distribution-Verification-key.asc \
&& apt-key add Bacula-4096-Distribution-Verification-key.asc \
&& rm Bacula-4096-Distribution-Verification-key.asc

COPY files/Bacula-Community.list /etc/apt/sources.list.d/Bacula-Community.list

RUN apt-get update \
&& apt-get -y install \
		bacula-postgresql \
		bacula-common \
		bacula-console \
		bacula-client \
		bacula-aligned

RUN for i in `ls /opt/bacula/bin`; do ln -s /opt/bacula/bin/$i /usr/sbin/$i; done
RUN rm /etc/apt/sources.list.d/Bacula-Community.list


