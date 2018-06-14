FROM ubuntu:16.04
MAINTAINER victor.you@nokia-sbell.com

ENV http_proxy=${http_proxy} \
    https_proxy=${https_proxy} \
    no_proxy=localhost,127.0.1.1,127.0.0.1,172.17.0.2
ENV STACK_HOME /opt/stack    

# install dependencies
RUN apt-get update \
    && apt-get install -y sudo git net-tools dnsutils inetutils-ping curl wget vim locales software-properties-common mysql-server

RUN add-apt-repository -y cloud-archive:queens \
    && apt-get install -y ubuntu-cloud-keyring  \
    && locale-gen "en_US.UTF-8" \
    && update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

RUN apt-get install linux-image-extra-$(uname -r) -y

# devstack installation preparation
RUN useradd -s /bin/bash -d ${STACK_HOME} -m stack
RUN echo "stack ALL=(ALL) NOPASSWD: ALL" | tee /etc/sudoers.d/stack \
    && echo "export http_proxy=${http_proxy}" >> ${STACK_HOME}/.profile \
    && echo "export https_proxy=${https_proxy}" >> ${STACK_HOME}/.profile \
    && echo "alias sudo='sudo -E'" >> ${STACK_HOME}/.profile \
    && echo "export no_proxy=localhost,127.0.1.1,127.0.0.1,172.17.0.2" >> ${STACK_HOME}/.profile
RUN cd ${STACK_HOME} && su -l stack -c "git clone https://git.openstack.org/openstack-dev/devstack ${STACK_HOME}/devstack"
RUN cd ${STACK_HOME} && su -l stack -c "sed -i 's@git://git.openstack.org@https://www.github.com@g' ${STACK_HOME}/devstack/stackrc"
COPY local.conf ${STACK_HOME}/devstack

# install devstack
#RUN cd ${STACK_HOME} && su -l stack -c "cd devstack && ./stack.sh"
