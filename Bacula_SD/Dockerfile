FROM ixxoid/bacula-common-ce:11.0.5-1

LABEL maintainer="ixxoid@bluewin.ch"

RUN for i in `ls /opt/bacula/bin`; do if test -z /usr/sbin/$i; then ln -s /opt/bacula/bin/$i /usr/sbin/$i; fi; done 

EXPOSE 9103/tcp

ENTRYPOINT ["bacula-sd"]

CMD ["-f", "-c", "/opt/bacula/etc/bacula-sd.conf"]