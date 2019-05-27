FROM nediiii/janus-gstreamer

LABEL maintainer "nediiii varndiiii@gmail.com"

# Setup demo environment variables
ENV DISPLAY=:0.0 \
    DISPLAY_WIDTH=1440 \
    DISPLAY_HEIGHT=900

# Install git, supervisor, VNC, & X11 packages
RUN apt-get update && \
    apt-get install -y \
    supervisor \
    xvfb \
    x11vnc \
    pulseaudio \
    xterm

RUN wget https://github.com/novnc/noVNC/archive/v1.1.0.tar.gz && \
    tar -zxvf v1.1.0.tar.gz && \
    rm v1.1.0.tar.gz && \
    mv noVNC-1.1.0 /root/noVNC && \
    wget https://github.com/novnc/websockify/archive/v0.8.0.tar.gz && \
    tar -zxvf v0.8.0.tar.gz && \
    rm v0.8.0.tar.gz && \
    mv websockify-0.8.0 /root/noVNC/utils/websockify 

COPY noVNC/index.html noVNC/streamingtest.js noVNC/janus.js /root/noVNC/
COPY noVNC/core/rfb.js /root/noVNC/core/rfb.js
COPY janus/janus.plugin.streaming.jcfg /opt/janus/etc/janus/janus.plugin.streaming.jcfg

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Modify the launch script 'ps -p'
# RUN sed -i -- "s/ps -p/ps -o pid | grep/g" /root/noVNC/utils/launch.sh

EXPOSE 8080 8088

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]

# docker build . --no-cache -t nediiii/novnc-continaer
# docker run --rm -d -p 8080:8080 -p 8088:8088 nediiii/novnc-continaer
