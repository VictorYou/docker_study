FROM centos:centos7
MAINTAINER victor.you@nokia-sbell.com

RUN yum install -y glibc.i686 libgcc.i686 libX11.i686
COPY SymantecEndpointProtection.zip /root/SymantecEndpointProtection.zip
RUN yum install -y unzip which wget bzip2 gcc
RUN unzip -d /root/SymantecEndpointProtection /root/SymantecEndpointProtection.zip
RUN chmod 777 /root/SymantecEndpointProtection/install.sh
RUN /root/SymantecEndpointProtection/install.sh -i

CMD ["cat"]
