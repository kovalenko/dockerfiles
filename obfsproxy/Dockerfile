FROM alpine
MAINTAINER AK <andrew.kovalenko@glera-games.com>

RUN set -xe \
    && apk add --update --no-cache build-base python3 python3-dev py3-pip git \
    && ln -sf python3 /usr/bin/python \
    && python3 -m pip install --no-cache-dir -e git+https://github.com/kovalenko/obfsproxy#egg=obfsproxy \
    && apk del build-base git python3-dev

ENV LOG_MIN_SEVERITY debug
ENV DATA_DIR /var/lib/obfsproxy
ENV PASSWORD XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
ENV DEST_ADDR localhost
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
