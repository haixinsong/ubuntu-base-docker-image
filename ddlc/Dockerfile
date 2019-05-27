FROM nediiii/novnc-continaer

LABEL maintainer "nediiii varndiiii@gmail.com"

RUN wget https://gitlab.com/nediiii/file-store/raw/master/DDLC-1.1.1-pc.tar.gz && \
    tar -zxvf DDLC-1.1.1-pc.tar.gz && rm DDLC-1.1.1-pc.tar.gz && \
    mv DDLC-1.1.1-pc /app/
    # EXPOSE 8080 8088
RUN sed -i 's/xterm/app\/DDLC.sh/g' /etc/supervisor/conf.d/supervisord.conf

# docker build . --no-cache -t nediiii/ddlc
# docker run --rm -d -p 8080:8080 -p 8088:8088 nediiii/ddlc
