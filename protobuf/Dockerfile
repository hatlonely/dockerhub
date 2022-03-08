FROM centos:centos7

RUN yum install -y wget unzip
RUN wget https://github.com/protocolbuffers/protobuf/releases/download/v3.19.4/protoc-3.19.4-linux-x86_64.zip && \
    unzip protoc-3.19.4-linux-x86_64.zip -d /usr/local && \
    rm -rf protoc-3.19.4-linux-x86_64.zip
RUN wget https://golang.org/dl/go1.16.15.linux-amd64.tar.gz && \
    tar -xzvf go1.16.15.linux-amd64.tar.gz --directory /usr/local && \
    rm -rf go1.16.15.linux-amd64.tar.gz
RUN yum install -y java
RUN wget https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/4.3.1/openapi-generator-cli-4.3.1.jar

ENV PATH="$PATH:/usr/local/bin:/usr/local/go/bin"
ENV GOBIN="/usr/local/go/bin"

RUN go install github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-grpc-gateway@v2.8.0
RUN go install github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-openapiv2@v2.8.0
RUN go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.27.1
RUN go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2.0
RUN go install github.com/gogo/protobuf/protoc-gen-gofast@v1.3.2
RUN go install github.com/envoyproxy/protoc-gen-validate@v0.6.7
RUN go install github.com/srikrsna/protoc-gen-gotag@v0.6.2

RUN yum install -y git
RUN git clone -b v2.8.0 --depth=1 https://github.com/grpc-ecosystem/grpc-gateway.git && \
    mkdir -p /usr/local/include/protoc-gen-openapiv2 && \
    cp -r grpc-gateway/protoc-gen-openapiv2/options /usr/local/include/protoc-gen-openapiv2/ && \
    rm -r grpc-gateway
RUN git clone -b v1.3.2 --depth=1 https://github.com/gogo/protobuf.git && \
    cp -r protobuf/gogoproto /usr/local/include/ && \
    rm -r protobuf
RUN git clone -b v0.6.2 --depth=1 https://github.com/srikrsna/protoc-gen-gotag.git && \
    cp -r protoc-gen-gotag/tagger /usr/local/include/ && \
    rm -r protoc-gen-gotag
RUN git clone -b v0.6.7 --depth=1 https://github.com/envoyproxy/protoc-gen-validate.git && \
    cp -r protoc-gen-validate/validate /usr/local/include && \
    rm -r protoc-gen-validate
RUN git clone -b common-protos-1_3_1 --depth=1 https://github.com/googleapis/googleapis.git && \
    cp -r googleapis/google /usr/local/include/ && \
    rm -r googleapis
