# Dockerfile for ariang based scratch
# Copyright (C) @ 2022-2023 KIMI360 <https://github.com/kimi360>
# Reference URL:
# https://github.com/emikulic/darkhttpd
# https://github.com/mayswind/AriaNg-DailyBuild

# Build environment
FROM alpine:3.21.3 AS build 
  
WORKDIR /apps

# Get AriaNG from github action
COPY ./src ./ariang

# Get darkhttpd from docker
RUN mkdir -p /apps/etc
COPY --from=kimi360/darkhttpd:1.14 /darkhttpd  /apps/darkhttpd
COPY --from=kimi360/darkhttpd:1.14 /etc/passwd /apps/etc/passwd
COPY --from=kimi360/darkhttpd:1.14 /etc/group  /apps/etc/group

FROM scratch
LABEL maintainer="KIMI360 <https://github.com/kimi360>"
COPY --from=build --chown=0:0 /apps /
EXPOSE 80
ENTRYPOINT ["/darkhttpd","/ariang", "--chroot", "--uid", "nobody", "--gid", "nobody"]
