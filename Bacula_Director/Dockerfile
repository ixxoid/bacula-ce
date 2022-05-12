FROM ixxoid/bacula-common-ce:11.0.6

LABEL maintainer="ixxoid@bluewin.ch"

EXPOSE 9101/tcp

ENTRYPOINT ["bacula-dir"]

CMD ["-f", "-c", "/opt/bacula/etc/bacula-dir.conf"]

