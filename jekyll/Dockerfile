FROM ruby:2.5.1
MAINTAINER re0marb1e re0marb1e@outlook.com
ENV REFRESHED_AT 2018-10-01
RUN gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
RUN gem install bundler jekyll
WORKDIR /srv/jekyll
