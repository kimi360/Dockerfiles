# Darkhttpd
[![icon][icon.license]][link.license]
[![icon][icon.darkhttpd]][link.darkhttpd.version]
[![icon][icon.docker.size]][link.docker.tags]
[![icon][icon.docker.pull]][link.docker.page]

## 简介
🍌 [Darkhttpd][darkhttpd] 是一个超小型静态http服务器。

## 说明
- 基于 [scratch] 镜像构建体积超小。
- 查看 [Dockerfile][dockerfile] 。

##  使用
###  快速开始

```shell
docker run -d \
  --name darkhttpd \
  --restart unless-stopped \
  -p 80:80 \
  -v ~/website:/var/www/htdocs:ro \
  kimi360/darkhttpd:latest
```

###  Docker-compose

```yaml
version: '3'
services:
  darkhttpd:
    image: kimi360/darkhttpd:latest
    container_name: darkhttpd
    restart: unless-stopped
    ports:
      - 80:80
    volumes:
      - ~/website:/var/www/htdocs:ro
```

##  引用
- [emikulic/darkhttpd][darkhttpd]

##  协议
- [MIT][link.license]

[icon.license]:            https://img.shields.io/github/license/kimi360/Dockerfiles
[icon.darkhttpd]:          https://img.shields.io/github/v/release/emikulic/darkhttpd?label=darkhttpd
[icon.docker.size]:        https://img.shields.io/docker/image-size/kimi360/darkhttpd/latest?color=yellow
[icon.docker.pull]:        https://img.shields.io/docker/pulls/kimi360/darkhttpd?color=orange

[link.license]:            https://github.com/kimi360/Dockerfiles/blob/main/LICENSE
[link.darkhttpd.version]:  https://github.com/emikulic/darkhttpd/releases
[link.docker.page]:        https://hub.docker.com/r/kimi360/darkhttpd
[link.docker.tags]:        https://hub.docker.com/r/kimi360/darkhttpd/tags

[darkhttpd]:               https://github.com/emikulic/darkhttpd
[scratch]:                 https://hub.docker.com/_/scratch
[dockerfile]:              https://github.com/kimi360/Dockerfiles/blob/main/darkhttpd/Dockerfile
