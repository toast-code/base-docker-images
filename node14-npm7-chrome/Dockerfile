FROM zenika/alpine-chrome
USER root
RUN apk add --no-cache tini make gcc g++ python3 git nodejs nodejs-npm
RUN npm i -g npm@7
USER chrome
ENTRYPOINT ["tini", "--"]
