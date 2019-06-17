# FROM aarch64/node:4.6-slim
ARG NODE_VERSION=8
FROM  arm64v8/node:${NODE_VERSION}-alpine 

COPY tmp/qemu-aarch64-static /usr/bin/qemu-aarch64-static

# Experimental ARMv8 support for Node-RED

# Home directory for Node-RED application source code.
RUN mkdir -p /usr/src/node-red

# User data directory, contains flows, config and nodes.
RUN mkdir /data

WORKDIR /usr/src/node-red

# Add node-red user so we aren't running as root.
RUN addgroup node-red && adduser node-red -G node-red -DH -h /usr/src/node-red \
    && chown -R node-red:node-red /data \
    && chown -R node-red:node-red /usr/src/node-red

RUN apk update && apk add --no-cache  bash linux-headers make gcc g++ python  \
	ca-certificates ffmpeg  tzdata\
	&& rm -rf /var/cache/*

ENV LANG="zh_CN.UTF-8" \
	LC_ALL="zh_CN.UTF-8" \
	TZ="Asia/Shanghai" 

USER node-red

# package.json contains Node-RED NPM module and node dependencies
COPY package.json /usr/src/node-red/
RUN npm install

# User configuration directory volume
EXPOSE 1880

# Environment variable holding file path for flows configuration
ENV FLOWS=flows.json

CMD ["npm", "start", "--", "--userDir", "/data"]
