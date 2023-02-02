# Frps
[![icon][icon.license]][link.license]
[![icon][icon.frp]][link.frp.version]
[![icon][icon.docker.size]][link.docker.tags]
[![icon][icon.docker.pull]][link.docker.page]

🍌 基于 [scratch] 构建的 [frps][frp] 镜像
##  简介
[frp] 是一个专注于内网穿透的高性能的反向代理应用，支持 TCP、UDP、HTTP、HTTPS 等多种协议。可以将内网服务以安全、便捷的方式通过具有公网 IP 节点的中转暴露到公网。

[frp] is a fast reverse proxy to help you expose a local server behind a NAT or firewall to the Internet. As of now, it supports TCP and UDP, as well as HTTP and HTTPS protocols, where requests can be forwarded to internal services by domain name.

##  说明
- 基于 [scratch] 镜像构建体积超小。
- 查看 [Dockerfile][dockerfile] 。

##  使用
###  快速开始

```shell
docker run -d \
  --name frps \
  --restart unless-stopped \
  -v ~/frps.ini:/frp/frps.ini \
  -p 7000:7000 \
  kimi360/frps:latest
```


###  Docker-compose

```yaml
version: '3'
services:
  frps:
    image: kimi360/frps:latest
    container_name: frps
    restart: unless-stopped
    ports:
      - 7000:7000
    volumes:
      - ~/frps.ini:/frp/frps.ini
```

## 引用
- [fatedier/frp][frp]

##  协议
- [MIT][link.license]

[icon.license]:            https://img.shields.io/github/license/kimi360/Dockerfiles
[icon.frp]:                https://img.shields.io/github/v/release/fatedier/frp?label=frp
[icon.docker.size]:        https://img.shields.io/docker/image-size/kimi360/frps/latest?color=yellow
[icon.docker.pull]:        https://img.shields.io/docker/pulls/kimi360/frps?color=orange

[link.license]:            https://github.com/kimi360/Dockerfiles/blob/main/LICENSE
[link.frp.version]:        https://github.com/fatedier/frp/releases
[link.docker.page]:        https://hub.docker.com/r/kimi360/frps
[link.docker.tags]:        https://hub.docker.com/r/kimi360/frps/tags

[frp]:                     https://github.com/fatedier/frp
[scratch]:                 https://hub.docker.com/_/scratch
[dockerfile]:              https://github.com/kimi360/Dockerfiles/blob/frpc/frps/Dockerfile

