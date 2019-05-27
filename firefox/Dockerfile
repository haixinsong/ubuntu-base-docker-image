FROM nediiii/novnc-continaer

LABEL maintainer "nediiii varndiiii@gmail.com"

RUN apt-get update && \
    apt-get install -y \
    firefox \
    ffmpeg \
    fonts-noto \
    fonts-noto-cjk \
    fonts-noto-color-emoji \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

# EXPOSE 8080 8088
RUN sed -i 's/xterm/firefox/g' /etc/supervisor/conf.d/supervisord.conf

# docker build . --no-cache -t nediiii/firefox
# docker run --rm -d -p 8080:8080 -p 8088:8088 nediiii/firefox
