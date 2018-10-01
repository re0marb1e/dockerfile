FROM node:8.12.0
MAINTAINER re0marb1e re0marb1e@outlook.com
ENV REFRESHED_AT 2018-10-01
RUN npm install drakov
ENV PATH ${PATH}:/node_modules/.bin
EXPOSE 3000
WORKDIR /blueprints
CMD drakov -f "*.md" --public true --watch
