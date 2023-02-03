# Homebox
[![icon][icon.license]][link.license]
[![icon][icon.homebox]][link.homebox.version]
[![icon][icon.docker.size]][link.docker.tags]
[![icon][icon.docker.pull]][link.docker.page]

🍌 基于 [scratch] 构建的 [homebox] 镜像
##  简介
[homebox] 家庭网络工具箱，主要用于组建家庭局域网时的一些调试、检测、压测工具。。

##  说明
- 基于 [scratch] 镜像构建体积超小。
- 查看 [Dockerfile][dockerfile] 。

##  使用
###  快速开始

```shell
docker run -d \
  --name homebox \
  --restart unless-stopped \
  -p 80:3300 \
  kimi360/homebox:latest
```

###  Docker-compose

```yaml
version: '3'
services:
  homebox:
    image: kimi360/homebox:latest
    container_name: homebox
    restart: unless-stopped
    ports:
      - 80:3300
```
##  截图
###  浅色主题
![screenshots][screenshots.light]
###  深色主题
![screenshots][screenshots.dark]

## 引用
- [XGHeaven/homebox][homebox]

##  协议
- [MIT][link.license]

[icon.license]:            https://img.shields.io/github/license/kimi360/Dockerfiles
[icon.homebox]:            https://img.shields.io/github/v/release/XGHeaven/homebox?label=homebox
[icon.docker.size]:        https://img.shields.io/docker/image-size/kimi360/homebox/latest?color=yellow
[icon.docker.pull]:        https://img.shields.io/docker/pulls/kimi360/homebox?color=orange

[link.license]:            https://github.com/kimi360/Dockerfiles/blob/main/LICENSE
[link.homebox.version]:    https://github.com/XGHeaven/homebox/releases
[link.docker.page]:        https://hub.docker.com/r/kimi360/homebox
[link.docker.tags]:        https://hub.docker.com/r/kimi360/homebox/tags

[screenshots.light]:       https://github.com/XGHeaven/homebox/raw/master/doc/light-theme.png
[screenshots.dark]:        https://github.com/XGHeaven/homebox/raw/master/doc/dark-theme.png

[homebox]:                 https://github.com/XGHeaven/homebox
[scratch]:                 https://hub.docker.com/_/scratch
[dockerfile]:              https://github.com/kimi360/Dockerfiles/blob/main/homebox/Dockerfile
