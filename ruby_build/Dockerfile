FROM ubuntu:16.04
MAINTAINER victor.you@nokia-sbell.com

ENV http_proxy=${http_proxy} \
    https_proxy=${https_proxy}

# install dependencies
RUN apt-get update
RUN apt-get install -y ruby ruby-dev zlib1g-dev gcc make git
RUN gem install rspec xml-mapping nokogiri
