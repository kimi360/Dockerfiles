# Dockerfile for darkhttpd
# Copyright (C) @ 2023 KIMI360 <https://github.com/kimi360>
# Reference URL:
# https://github.com/emikulic/darkhttpd

# Build environment
FROM alpine:3.17.2 AS build 

RUN apk add --no-cache \
  build-base=~0.5

WORKDIR /src

# Get darkhttpd from github action
COPY ./src .

# Set build environment
ENV CFLAGS=" \
  -static                                 \
  -O2                                     \
  -flto                                   \
  -D_FORTIFY_SOURCE=2                     \
  -fstack-clash-protection                \
  -fstack-protector-strong                \
  -pipe                                   \
  -Wall                                   \
  -Werror=format-security                 \
  -Werror=implicit-function-declaration   \
  -Wl,-z,defs                             \
  -Wl,-z,now                              \
  -Wl,-z,relro                            \
  -Wl,-z,noexecstack                      \
"

# Make darkhttpd and collect files into apps folder
RUN make  darkhttpd-static                \
 && strip darkhttpd-static                \
 && mkdir -p /apps/etc                    \
 && mkdir -p /apps/var/www/htdocs         \
 && mv darkhttpd-static /apps/darkhttpd   \
 && mv passwd           /apps/etc         \
 && mv group            /apps/etc 

FROM scratch
LABEL maintainer="KIMI360 <https://github.com/kimi360>"
COPY --from=build --chown=0:0 /apps /
EXPOSE 80
ENTRYPOINT ["/darkhttpd","/var/www/htdocs", "--chroot", "--uid", "nobody", "--gid", "nobody"]
