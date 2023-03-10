# Darkhttpd
[![icon][icon.license]][link.license]
[![icon][icon.darkhttpd]][link.darkhttpd.version]
[![icon][icon.docker.size]][link.docker.tags]
[![icon][icon.docker.pull]][link.docker.page]

## ç®ä»
ð [Darkhttpd][darkhttpd] æ¯ä¸ä¸ªè¶å°åéæhttpæå¡å¨ã

## è¯´æ
- åºäº [scratch] éåæå»ºä½ç§¯è¶å°ã
- æ¥ç [Dockerfile][dockerfile] ã

##  ä½¿ç¨
###  å¿«éå¼å§

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

##  å¼ç¨
- [emikulic/darkhttpd][darkhttpd]

##  åè®®
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
