FROM nediiii/golang:ubuntu-18.04

# dep for mongo graphql gin

RUN go get -v go.mongodb.org/mongo-driver/mongo;exit 0
RUN go get -v github.com/graphql-go/graphql
RUN go get -v github.com/graphql-go/handler
RUN go get -v github.com/gin-gonic/gin
RUN go get -v github.com/gin-contrib/cors

# docker build . --no-cache -t nediiii/dep:ubuntu-18.04
