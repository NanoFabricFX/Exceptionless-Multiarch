# A minimal Docker image with Node and Puppeteer
#
# Based upon:
# https://github.com/GoogleChrome/puppeteer/blob/master/docs/troubleshooting.md#running-puppeteer-in-docker

ARG PUPPETEER_NODE_VERSION
FROM node:${PUPPETEER_NODE_VERSION}-slim

RUN  apt-get update \
     && apt install -y wget --no-install-recommends \
     && apt install -y chromium --no-install-recommends \
     && rm -rf /var/lib/apt/lists/* \
     && wget --quiet https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh -O /usr/sbin/wait-for-it.sh \
     && chmod +x /usr/sbin/wait-for-it.sh \
     && apt autoremove -y \
     && apt clean

# Install Puppeteer under /node_modules so it's available system-wide
ADD package.json package-lock.json /
RUN npm install
