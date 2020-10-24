FROM ubuntu:latest
MAINTAINER victor.you@nokia-sbell.com

RUN apt-get update
RUN apt install -y tzdata
RUN echo "Asia/Beijing" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata
RUN apt install -y \
  curl \
  expect \
  ldap-utils

RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
RUN cat > /etc/apt/sources.list.d/kubernetes.list <<EOF \
deb https://apt.kubernetes.io/ kubernetes-xenial main \
EOF

RUN apt install -y \
  kubectl

ENTRYPOINT ["/bin/sh", "-c"]
