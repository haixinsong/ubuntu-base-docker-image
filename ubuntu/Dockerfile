FROM ubuntu:18.04 as builder

RUN sed -i 's/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list && \
    sed -i 's/security.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list

ENV TZ Asia/Shanghai

RUN apt-get update && \
    apt-get install -y tzdata && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone

# ------------------------------------------------------------------------------------------------

FROM ubuntu:18.04

LABEL maintainer="nediiii <varnediiii@gmail.com>"

RUN sed -i 's/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list && \
    sed -i 's/security.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list \
    && \
    apt-get update && \
    apt-get install --no-install-recommends --no-install-suggests -y ca-certificates && \
    rm -rf /var/lib/apt/lists/* \
    && \
    sed -i 's/http/https/g' /etc/apt/sources.list

# copy timezone file to set time and timezone
COPY --from=builder /etc/localtime /etc/timezone /etc/

# CMD ["/bin/bash"]

# docker build . --no-cache -t nediiii/ubuntu:18.04
