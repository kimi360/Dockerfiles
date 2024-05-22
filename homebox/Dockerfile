# Dockerfile for homebox based scratch
# Copyright (C) @ 2023 KIMI360 <https://github.com/kimi360>
# Reference URL:
# https://github.com/XGHeaven/homebox

# Build environment
FROM alpine:3.20.0 AS build 
ARG TARGETOS
ARG TARGETARCH
ARG HOMEBOX_VERSION

WORKDIR /src
RUN mkdir -p /homebox \
 && HOMEBOX_PACKAGE="server-${TARGETOS}-${TARGETARCH}" \
 && HOMEBOX_URL="https://github.com/XGHeaven/homebox/releases/download/v${HOMEBOX_VERSION}/${HOMEBOX_PACKAGE}.tar.gz" \
 && wget --no-check-certificate --no-verbose -c "${HOMEBOX_URL}" \
 && tar zxvf "${HOMEBOX_PACKAGE}".tar.gz \
 && mv  "${HOMEBOX_PACKAGE}" /homebox/server

FROM scratch
LABEL maintainer="KIMI360 <https://github.com/kimi360>"
COPY --from=build --chown=0:0 /homebox /
EXPOSE 3300
ENTRYPOINT ["./server"]
