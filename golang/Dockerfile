FROM nediiii/dev:ubuntu-18.04 as builder

ENV GO_VERSION=1.13.4

RUN apt-get update && \
    apt-get install --no-install-recommends --no-install-suggests -yyq wget && \
    wget https://dl.google.com/go/go${GO_VERSION}.linux-amd64.tar.gz && \
    tar -C  /usr/local -xzf go${GO_VERSION}.linux-amd64.tar.gz


FROM nediiii/dev:ubuntu-18.04

COPY --from=builder /usr/local/go /usr/local/go

ENV PATH=$PATH:/usr/local/go/bin

ENV GOPATH="/root/go"

RUN mkdir -p "$GOPATH" "$GOPATH/src" "$GOPATH/bin" && \
    chmod -R 777 "$GOPATH"

ENV PATH $GOPATH/bin:$PATH

WORKDIR $GOPATH

# docker build . --no-cache -t nediiii/golang:ubuntu-18.04
