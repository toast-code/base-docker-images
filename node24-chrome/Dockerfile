FROM node:24.16.0-bookworm-slim

LABEL maintainer="ToastCode"
LABEL org.opencontainers.image.title="toastcode-node-chrome"
LABEL org.opencontainers.image.description="Node 24.16.0 with pinned Debian Chromium for Puppeteer"

ARG REFRESHED_AT
ARG CHROMIUM_VERSION=150.0.7871.100-1~deb12u1

ENV REFRESHED_AT=$REFRESHED_AT
ENV PUPPETEER_SKIP_DOWNLOAD=true
ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=1
ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/google-chrome

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apt-get update -qq \
  && apt-get install -qq --no-install-recommends \
    ca-certificates \
    curl \
    chromium=${CHROMIUM_VERSION} \
  && apt-mark hold chromium chromium-common \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* \
  && ln -sf /usr/bin/chromium /usr/bin/google-chrome \
  && node --version \
  && npm --version \
  && chromium --version \
  && google-chrome --version
