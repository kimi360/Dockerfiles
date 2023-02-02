# AriaNg
[![icon][icon.license]][link.license]
[![icon][icon.ariang]][link.ariang.version]
[![icon][icon.darkhttpd]][link.darkhttpd.version]
[![icon][icon.docker.size]][link.docker.tags]
[![icon][icon.docker.pull]][link.docker.page]

🍌 基于 [scratch] 构建的 [AriaNg][ariang] 镜像
## 简介
[AriaNg][ariang] 是一个让 [aria2] 更容易使用的现代 Web 前端. [AriaNg][ariang] 使用纯 html & javascript 开发, 所以其不需要任何编译器或运行环境. 您只要将 [AriaNg][ariang] 放在您的 Web 服务器里并在浏览器中打开即可使用. [AriaNg][ariang] 使用响应式布局, 支持各种计算机或移动设备.

[AriaNg][ariang] is a modern web frontend making [aria2] easier to use. [AriaNg][ariang] is written in pure html & javascript, thus it does not need any compilers or runtime environment. You can just put [AriaNg][ariang] in your web server and open it in your browser. [AriaNg][ariang] uses responsive layout, and supports any desktop or mobile devices.

## 说明
- 基于 [scratch] 镜像构建体积超小。
- 查看 [Dockerfile][dockerfile] 。

## 使用
### 快速开始
```shell
docker run -d \
  --name ariang \
  --restart unless-stopped \
  -p 80:80 \
  kimi360/ariang:latest
```

### 启用日志 | 设置时区 | 健康检查
```shell
#使用第三方健康检查
wget https://github.com/chrisaxiom/docker-health-check/blob/master/docker-health-check?raw=true -O healthcheck
chmod a+x healthcheck
docker run -d \
  --name ariang \
  --restart unless-stopped \
  -v ~/logs:/logs \
  -v ~/healthcheck:/healthcheck \
  -v /usr/share/zoneinfo/Asia/Shanghai:/etc/localtime \
  -p 80:80 \
  --health-cmd="/healthcheck -url=http://127.0.0.1" \
  kimi360/ariang:latest \
  --log /logs/access.log
```

### Docker-compose
```yaml
version: '3'
services:
  ariang:
    image: kimi360/ariang
    container_name: ariang
    restart: unless-stopped
    ports:
      - 80:80
    volumes:
      - ~/logs:/logs
      - ~/healthcheck:/healthcheck
      - /usr/share/zoneinfo/Asia/Shanghai:/etc/localtime
    healthcheck:
      test: ["CMD", "/healthcheck", "-url=http://127.0.0.1"]
    command: ["--log","/logs/access.log"]
```

## 截图
### 桌面端
![screenshots][screenshots.desktop]
### 移动端
![screenshots][screenshots.mobile]

## 引用
- [mayswind/AriaNg][ariang]
- [emikulic/darkhttpd][darkhttpd]
- [chrisaxiom/docker-health-check][healthcheck]

## 协议
- [MIT][link.license]

[icon.license]:            https://img.shields.io/github/license/kimi360/Dockerfiles
[icon.ariang]:             https://img.shields.io/github/v/release/mayswind/AriaNg?label=AriaNg
[icon.darkhttpd]:          https://img.shields.io/github/v/release/emikulic/darkhttpd?label=darkhttpd
[icon.docker.size]:        https://img.shields.io/docker/image-size/kimi360/ariang/latest?color=yellow
[icon.docker.pull]:        https://img.shields.io/docker/pulls/kimi360/ariang?color=orange

[link.license]:            https://github.com/kimi360/Dockerfiles/blob/main/LICENSE
[link.ariang.version]:     https://github.com/mayswind/AriaNg/releases
[link.darkhttpd.version]:  https://github.com/emikulic/darkhttpd/releases
[link.docker.page]:        https://hub.docker.com/r/kimi360/ariang
[link.docker.tags]:        https://hub.docker.com/r/kimi360/ariang/tags

[screenshots.desktop]:     https://raw.githubusercontent.com/mayswind/AriaNg-WebSite/master/screenshots/desktop.png
[screenshots.mobile]:      https://raw.githubusercontent.com/mayswind/AriaNg-WebSite/master/screenshots/mobile.png

[aria2]:                   https://github.com/aria2/aria2
[ariang]:                  https://github.com/mayswind/AriaNg
[scratch]:                 https://hub.docker.com/_/scratch
[darkhttpd]:               https://github.com/emikulic/darkhttpd
[dockerfile]:              https://github.com/kimi360/Dockerfiles/blob/main/ariang/Dockerfile
[healthcheck]:             https://github.com/chrisaxiom/docker-health-check
