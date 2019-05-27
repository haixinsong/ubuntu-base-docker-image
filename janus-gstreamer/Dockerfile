FROM nediiii/janus

LABEL maintainer "nediiii varndiiii@gmail.com"

# gstreamer1.0-plugins-bad need libsrtp ,which is no compatible with janus webrtc server
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    libgstreamer1.0-0 \
    gstreamer1.0-plugins-base \
    gstreamer1.0-plugins-good \
    # gstreamer1.0-plugins-bad \
    # gstreamer1.0-plugins-ugly \
    gstreamer1.0-libav \
    gstreamer1.0-doc \
    gstreamer1.0-tools \
    gstreamer1.0-x \
    gstreamer1.0-alsa \
    gstreamer1.0-gl \
    gstreamer1.0-gtk3 \
    gstreamer1.0-qt5 \
    gstreamer1.0-pulseaudio

# docker build . --no-cache -t nediiii/janus-gstreamer
