# Dockerfile for frpc based scratch
# Copyright (C) @ 2023 KIMI360 <https://github.com/kimi360>
# Reference URL:
# https://github.com/fatedier/frp

# Build environment
FROM alpine:3.18.4 AS build 
ARG TARGETOS
ARG TARGETARCH
ARG FRP_VERSION

WORKDIR /src
RUN mkdir -p /frp \
 && FRP_PACKAGE="frp_${FRP_VERSION}_${TARGETOS}_${TARGETARCH}" \
 && FRP_URL="https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/${FRP_PACKAGE}.tar.gz" \
 && wget --no-check-certificate --no-verbose -c "${FRP_URL}" \
 && tar zxvf "${FRP_PACKAGE}".tar.gz \
 && mv "${FRP_PACKAGE}"/frpc     /frp/frpc \
 && mv "${FRP_PACKAGE}"/frpc.ini /frp/frpc.ini

FROM scratch
LABEL maintainer="KIMI360 <https://github.com/kimi360>"
COPY --from=build --chown=0:0 /frp /frp
ENTRYPOINT ["/frp/frpc","-c","/frp/frpc.ini"]
