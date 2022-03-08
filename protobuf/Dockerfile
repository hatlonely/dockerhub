FROM centos:centos7

RUN yum install -y wget unzip
RUN wget https://github.com/protocolbuffers/protobuf/releases/download/v3.19.4/protoc-3.19.4-linux-x86_64.zip && \
    unzip protoc-3.19.4-linux-x86_64.zip -d /usr/local
RUN wget https://golang.org/dl/go1.16.15.linux-amd64.tar.gz && \
    tar -xzvf go1.16.15.linux-amd64.tar.gz
RUN yum install -y java
RUN wget https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/4.3.1/openapi-generator-cli-4.3.1.jar

ENV PATH="$PATH:/usr/local/go/bin"

RUN go get -d github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-grpc-gateway@v2.8.0
RUN go get -d github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-openapiv2@v2.8.0
RUN go get -d google.golang.org/protobuf/cmd/protoc-gen-go@v1.27.1
RUN go get -d google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2.0
RUN go get -d github.com/gogo/protobuf/protoc-gen-gofast@v1.3.2
RUN go get -d github.com/envoyproxy/protoc-gen-validate@v0.6.7
