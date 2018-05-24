FROM yfoelling/yair

LABEL maintainer="komattaka <komazaki.1002@gmail.com>"

ARG VCS_REF
ARG BUILD_DATE

# Metadata
LABEL org.label-schema.url="https://github.com/komattaka/" \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-type="Git" \
      org.label-schema.vcs-url="https://github.com/komattaka/clair-client" \
      org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.docker.dockerfile="./yair/Dockerfile"

ENV REGISTRY_HOST="registry.hub.docker.com"
ENV CLAIR_HOST="clair:6060"
ENV OUTPUT_FORMAT="table"
ENV FAIL_ON_SCORE="824"
ENV ANALYZE_CONTAINER=""

ADD config.yaml.template /opt/yair/config/

RUN apk --no-cache add libintl \
  && apk --no-cache add --virtual .gettext gettext \
  && cp /usr/bin/envsubst /usr/local/bin/envsubst \
  && apk del .gettext

ENTRYPOINT /bin/sh -c envsubst < /opt/yair/config/config.yaml.template > /opt/yair/config/config.yaml && /opt/yair/yair.py ${ANALYZE_CONTAINER}
