# Frpc
[![icon][icon.license]][link.license]
[![icon][icon.frp]][link.frp.version]
[![icon][icon.docker.size]][link.docker.tags]
[![icon][icon.docker.pull]][link.docker.page]

ð åºäº [scratch] æå»ºç [frpc][frp] éå
##  ç®ä»
[frp] æ¯ä¸ä¸ªä¸æ³¨äºåç½ç©¿éçé«æ§è½çååä»£çåºç¨ï¼æ¯æ TCPãUDPãHTTPãHTTPS ç­å¤ç§åè®®ãå¯ä»¥å°åç½æå¡ä»¥å®å¨ãä¾¿æ·çæ¹å¼éè¿å·æå¬ç½ IP èç¹çä¸­è½¬æ´é²å°å¬ç½ã

[frp] is a fast reverse proxy to help you expose a local server behind a NAT or firewall to the Internet. As of now, it supports TCP and UDP, as well as HTTP and HTTPS protocols, where requests can be forwarded to internal services by domain name.

##  è¯´æ
- åºäº [scratch] éåæå»ºä½ç§¯è¶å°ã
- æ¥ç [Dockerfile][dockerfile] ã

##  ä½¿ç¨
###  å¿«éå¼å§

```shell
docker run -d \
  --name frpc \
  --restart unless-stopped \
  -v ~/frpc.ini:/frp/frpc.ini \
  kimi360/frpc:latest
```


###  Docker-compose

```yaml
version: '3'
services:
  frpc:
    image: kimi360/frpc:latest
    container_name: frpc
    restart: unless-stopped
    volumes:
      - ~/frpc.ini:/frp/frpc.ini
```

## å¼ç¨
- [fatedier/frp][frp]

##  åè®®
- [MIT][link.license]

[icon.license]:            https://img.shields.io/github/license/kimi360/Dockerfiles
[icon.frp]:                https://img.shields.io/github/v/release/fatedier/frp?label=frp
[icon.docker.size]:        https://img.shields.io/docker/image-size/kimi360/frpc/latest?color=yellow
[icon.docker.pull]:        https://img.shields.io/docker/pulls/kimi360/frpc?color=orange

[link.license]:            https://github.com/kimi360/Dockerfiles/blob/main/LICENSE
[link.frp.version]:        https://github.com/fatedier/frp/releases
[link.docker.page]:        https://hub.docker.com/r/kimi360/frpc
[link.docker.tags]:        https://hub.docker.com/r/kimi360/frpc/tags

[frp]:                     https://github.com/fatedier/frp
[scratch]:                 https://hub.docker.com/_/scratch
[dockerfile]:              https://github.com/kimi360/Dockerfiles/blob/main/frpc/Dockerfile
