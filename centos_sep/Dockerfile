FROM centos
MAINTAINER victor.you@nokia-sbell.com

RUN yum install -y unzip
RUN yum install -y glibc.i686 libgcc.i686 libX11.i686
COPY SymantecEndpointProtection.zip /root/SymantecEndpointProtection.zip
RUN unzip -d /root/SymantecEndpointProtection /root/SymantecEndpointProtection.zip

CMD ["cat"]
