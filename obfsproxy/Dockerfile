FROM python:2.7.18-alpine3.11
MAINTAINER AK <andrew.kovalenko@glera-games.com>

RUN set -xe \
    && apk add --update --no-cache build-base \
    && python -m pip install --no-cache-dir obfsproxy \
    && apk del build-base

ENV LOG_SEVERITY debug
ENV DATA_DIR /var/lib/obfsproxy
ENV PASSWORD XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
ENV DEST_ADDR localhost:1194
ENV RUN_MODE server
ENV LISTEN_ADDR 0.0.0.0:4911

CMD obfsproxy --log-min-severity=$LOG_SEVERITY \
              --data-dir=$DATA_DIR \
              scramblesuit \
              --password=$PASSWORD \
              --dest=$DEST_ADDR \
              $RUN_MODE \
              $LISTEN_ADDR
