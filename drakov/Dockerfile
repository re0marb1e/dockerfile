FROM node:8.4.0
MAINTAINER re0marb1e re0marb1e@outlook.com
ENV REFRESHED_AT 2018-10-01
RUN npm install -g cnpm --registry=https://registry.npm.taobao.org
RUN cnpm install -g drakov
EXPOSE 3000
WORKDIR /blueprints
CMD drakov -f "*.md" --public true --watch
