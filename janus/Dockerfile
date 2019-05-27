FROM nediiii/ubuntu:18.04

LABEL maintainer "nediiii varndiiii@gmail.com"

RUN apt-get update && \
    apt-get install -y \
    libmicrohttpd-dev \
    libjansson-dev \
    libssl-dev \
    libsofia-sip-ua-dev \
    libglib2.0-dev \
    libopus-dev \
    libogg-dev \
    libcurl4-openssl-dev \
    liblua5.3-dev \
    libconfig-dev \
    pkg-config \
    gengetopt \
    libtool \
    automake \
    cmake \
    gtk-doc-tools \
    wget \
    && \
    # libnice
    cd /tmp && \
    wget https://github.com/libnice/libnice/archive/0.1.16.tar.gz && \
    tar -zxvf 0.1.16.tar.gz && \
    cd /tmp/libnice-0.1.16 && \
    ./autogen.sh && \
    ./configure --prefix=/usr && \
    make && make install \
    && \
    # libsrtp
    cd /tmp && \
    wget https://github.com/cisco/libsrtp/archive/v2.2.0.tar.gz && \
    tar -zxvf v2.2.0.tar.gz && \
    cd /tmp/libsrtp-2.2.0 && \
    ./configure --prefix=/usr --enable-openssl && \
    make shared_library && make install \
    && \
    # libwebsocket
    cd /tmp && \
    wget https://github.com/warmcat/libwebsockets/archive/v3.1.0.tar.gz && \
    tar -zxvf v3.1.0.tar.gz && \
    cd /tmp/libwebsockets-3.1.0 && \
    mkdir build && \
    cd build && \
    cmake -DLWS_MAX_SMP=1 -DCMAKE_INSTALL_PREFIX:PATH=/usr -DCMAKE_C_FLAGS="-fpic" .. && \
    make && make install \
    && \
    # janus
    cd /tmp && \
    wget https://github.com/meetecho/janus-gateway/archive/v0.7.1.tar.gz && \
    tar -zxvf v0.7.1.tar.gz && \
    cd /tmp/janus-gateway-0.7.1 && \
    ./autogen.sh && \
    ./configure --prefix=/opt/janus --disable-data-channels --disable-rabbitmq --disable-mqtt && \
    make && make install && make configs \
    && \
    rm -rf /tmp/* /var/lib/apt/lists/*

# docker build . --no-cache -t nediiii/janus
