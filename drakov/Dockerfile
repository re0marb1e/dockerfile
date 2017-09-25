FROM node:8.4.0
MAINTAINER Xiaotian Zhao "zhxt1016@gmail.com"
ENV REFRESHED_AT 2017-09-09
RUN npm install -g cnpm --registry=https://registry.npm.taobao.org
RUN cnpm install -g drakov
EXPOSE 3000
WORKDIR /blueprints
CMD drakov -f "*.md" --public true --watch
