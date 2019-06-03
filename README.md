# Node-RED-Docker

[原版英文文档](./README_EN.md)

NodeRed docker 镜像,此版本与官方镜像区别如下:
* 添加**gyp环境**依赖的`gcc` `make` `g++` `python`
* 添加`ffmpeg`,方便调用音视频

```
docker run -it -p 1880:1880 --name mynodered smarthomefans/node-red-docker
```


镜像
---

目前提供了两个版本,基于`debian:jessie`和`node:alpine`,且分别提供node `v8`和`v10`两个版本,默认版本为**v8**

- **latest** - uses [official Node.JS v8 base image](https://hub.docker.com/_/node/).
- **slim** uses [Alpine Linux base image](https://hub.docker.com/r/mhart/alpine-node/).

