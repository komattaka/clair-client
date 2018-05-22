FROM alpine

LABEL maintainer="komattaka <komazaki.1002@gmail.com>"

ARG VCS_REF
ARG BUILD_DATE

# Metadata
LABEL org.label-schema.url="https://github.com/komattaka/" \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-type="Git" \
      org.label-schema.vcs-url="https://github.com/komattaka/clair-client" \
      org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.docker.dockerfile="./klar/Dockerfile"

ARG KLAR_VERSION=2.0.2

RUN apk add --update ca-certificates \
  && apk add --update -t deps wget \
  && wget -O /usr/local/bin/klar https://github.com/optiopay/klar/releases/download/v${KLAR_VERSION}/klar-${KLAR_VERSION}-linux-amd64 \
  && chmod +x /usr/local/bin/klar \
  && apk del --purge deps \
  && rm /var/cache/apk/*

ENTRYPOINT ["/usr/local/bin/klar"]
CMD [""]
