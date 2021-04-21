FROM centos:centos8

RUN dnf install -y wget gcc gcc-c++ make git curl jq
RUN wget https://github.com/protocolbuffers/protobuf/releases/download/v3.15.5/protobuf-all-3.15.5.tar.gz && \
    tar -xzvf protobuf-all-3.15.5.tar.gz && \
    cd protobuf-3.15.5 && ./configure && make -j8 && make install

# https://openapi-generator.tech/docs/generators/go
RUN dnf install -y java
RUN wget https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/4.3.1/openapi-generator-cli-4.3.1.jar
RUN wget https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/5.0.1/openapi-generator-cli-5.0.1.jar

# https://goswagger.io/install.html
RUN curl -o /usr/local/bin/swagger -L'#' "https://github.com/go-swagger/go-swagger/releases/download/v0.26.1/swagger_linux_amd64" && \
    chmod +x /usr/local/bin/swagger

RUN wget https://dl.google.com/go/go1.14.15.linux-amd64.tar.gz && \
    tar -xzvf go1.14.15.linux-amd64.tar.gz

RUN wget https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/5.1.0/openapi-generator-cli-5.1.0.jar

ENV PATH="$PATH:/go/bin:/usr/local/go/bin"
ENV GOPATH="/usr/local/go"
ENV GOROOT="/go"

# https://github.com/grpc-ecosystem/grpc-gateway
RUN go get -u -v \
    github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway \
    github.com/grpc-ecosystem/grpc-gateway/protoc-gen-openapiv2 \
    google.golang.org/protobuf/cmd/protoc-gen-go \
    google.golang.org/grpc/cmd/protoc-gen-go-grpc \
    github.com/gogo/protobuf/protoc-gen-gofast


RUN go get -u github.com/srikrsna/protoc-gen-gotag

