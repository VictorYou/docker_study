FROM ubuntu:latest
MAINTAINER victor.you@nokia-sbell.com

RUN apt-get update
RUN apt install -y tzdata
RUN echo "Asia/Beijing" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata
RUN apt install -y \
  curl \
  expect \
  gnupg \
  ldap-utils \
  telnet

RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
RUN /bin/echo -e 'deb https://apt.kubernetes.io/ kubernetes-xenial main'\
> /etc/apt/sources.list.d/kubernetes.list

RUN cat /etc/apt/sources.list.d/kubernetes.list
RUN apt-get update
RUN apt install -y \
  kubectl

ENTRYPOINT ["/bin/sh", "-c"]
