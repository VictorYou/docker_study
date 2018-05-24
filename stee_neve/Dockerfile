FROM archive.docker-registry.eecloud.nsn-net.net/jneve/neveexec18:latest
MAINTAINER victor.you@nokia-sbell.com

RUN pip install robotframework-ride

RUN echo "deb http://archive.ubuntu.com/ubuntu trusty main universe" | tee /etc/apt/sources.list.d/trusty-copies.list \
    && apt-get update  \
    && apt-get install -y python-wxgtk2.8 \
    && rm /etc/apt/sources.list.d/trusty-copies.list \
    && apt-get update

RUN mkdir $HOME/.vnc \
    && /bin/echo -e "arthur\narthur" | vncpasswd $HOME/.vnc/passwd \
    && chmod 600 $HOME/.vnc/passwd
