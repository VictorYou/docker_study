FROM stee_docker:1.0
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

RUN /bin/echo -e "#!/bin/bash\nvncserver -geometry 1600x1200 -ZlibLevel=9 -AlwaysShared=on\nsupervisord -n" > start.sh && chmod u+x start.sh

CMD ["/start.sh"]
