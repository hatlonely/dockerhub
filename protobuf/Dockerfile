FROM centos:centos7

RUN yum install -y wget gcc gcc-c++ make git
RUN wget https://github.com/protocolbuffers/protobuf/releases/download/v3.15.5/protobuf-all-3.15.5.tar.gz && \
    tar -xzvf protobuf-all-3.15.5.tar.gz && \
    cd protobuf-3.15.5 && ./configure && make -j8 && make install
RUN wget https://golang.org/dl/go1.14.15.linux-amd64.tar.gz && \
    tar -xzvf go1.14.15.linux-amd64.tar.gz

ENV PATH="$PATH:/go/bin:/usr/local/go/bin"
ENV GOPATH="/usr/local/go"
ENV GOROOT="/go"

RUN go get -u \
    github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway \
    github.com/grpc-ecosystem/grpc-gateway/protoc-gen-openapiv2 \
    google.golang.org/protobuf/cmd/protoc-gen-go \
    google.golang.org/grpc/cmd/protoc-gen-go-grpc \
    github.com/gogo/protobuf/protoc-gen-gofast

RUN yum install -y java
RUN wget https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/4.3.1/openapi-generator-cli-4.3.1.jar
