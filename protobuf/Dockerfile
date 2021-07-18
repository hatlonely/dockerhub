FROM centos:centos7

RUN yum install -y wget gcc gcc-c++ make git
RUN wget https://github.com/protocolbuffers/protobuf/releases/download/v3.15.5/protobuf-all-3.15.5.tar.gz && \
    tar -xzvf protobuf-all-3.15.5.tar.gz && \
    cd protobuf-3.15.5 && ./configure && make -j8 && make install
RUN wget https://golang.org/dl/go1.14.15.linux-amd64.tar.gz && \
    tar -xzvf go1.14.15.linux-amd64.tar.gz

RUN yum install -y java
RUN wget https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/4.3.1/openapi-generator-cli-4.3.1.jar

ENV PATH="$PATH:/go/bin:/usr/local/go/bin"
ENV GOPATH="/usr/local/go"
ENV GOROOT="/go"

RUN go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway@v2.3.0
RUN go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-openapiv2@v2.3.0
RUN go get -u google.golang.org/protobuf/cmd/protoc-gen-go
RUN go get -u google.golang.org/grpc/cmd/protoc-gen-go-grpc
RUN go get -u github.com/gogo/protobuf/protoc-gen-gofast
