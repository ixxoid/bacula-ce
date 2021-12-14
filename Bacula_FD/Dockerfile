FROM ixxoid/bacula-common-ce:11.0.5-1

LABEL maintainer="ixxoid@bluewin.ch"

EXPOSE 9102/tcp

ENTRYPOINT ["bacula-fd"]

CMD ["-f", "-c", "/opt/bacula/etc/bacula-fd.conf"]