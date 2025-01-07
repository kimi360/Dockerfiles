# Dockerfile for frps based scratch
# Copyright (C) @ 2023 KIMI360 <https://github.com/kimi360>
# Reference URL:
# https://github.com/fatedier/frp

# Build environment
FROM alpine:3.21.1 AS build 
ARG TARGETOS
ARG TARGETARCH
ARG FRP_VERSION

WORKDIR /src
RUN mkdir -p /frp \
 && FRP_PACKAGE="frp_${FRP_VERSION}_${TARGETOS}_${TARGETARCH}" \
 && FRP_URL="https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/${FRP_PACKAGE}.tar.gz" \
 && wget --no-check-certificate --no-verbose -c "${FRP_URL}" \
 && tar zxvf "${FRP_PACKAGE}".tar.gz \
 && mv "${FRP_PACKAGE}"/frps     /frp/frps \
 && mv "${FRP_PACKAGE}"/frps.toml /frp/frps.toml

FROM scratch
LABEL maintainer="KIMI360 <https://github.com/kimi360>"
COPY --from=build --chown=0:0 /frp /frp
EXPOSE 7000
ENTRYPOINT ["/frp/frps","-c","/frp/frps.toml"]
