FROM alpine
MAINTAINER AK <andrew.kovalenko@glera-games.com>

RUN set -xe \
    && apk add --update --no-cache build-base python3 py3-pip \
    && ln -sf python3 /usr/bin/python \
    && pip install --no-cache-dir obfsproxy \
    && apk del build-base

ENV LOG_MIN_SEVERITY info
ENV DATA_DIR /var/lib/obfsproxy
ENV PASSWORD XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
ENV DEST_ADDR openvpn
ENV DEST_PORT 1194
ENV RUN_MODE server
ENV LISTEN_ADDR 0.0.0.0
ENV LISTEN_PORT 4911

CMD obfsproxy --log-min-severity=$LOG_MIN_SEVERITY \
              --data-dir=$DATA_DIR \
              scramblesuit \
              --password=$PASSWORD \
              --dest=$DEST_ADDR:$DEST_PORT \
              $RUN_MODE \
              $LISTEN_ADDR:$LISTEN_PORT
