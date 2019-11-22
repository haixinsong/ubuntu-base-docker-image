FROM nediiii/ubuntu:18.04

RUN apt-get update && \
    apt-get install --no-install-recommends --no-install-suggests -y \
    build-essential \
    git \
    && \
    rm -rf /var/lib/apt/lists/*

# docker build . --no-cache -t nediiii/dev:ubuntu-18.04
