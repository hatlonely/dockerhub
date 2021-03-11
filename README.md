# dockerhub

一些通用镜像

## protobuf

protobuf 文件编译镜像

在 Makefile 中添加如下代码编译

```Makefile
.PHONY: codegen
codegen: api/api.proto
	if [ ! -z "$(shell docker ps --filter name=protobuf -q)" ]; then \
		docker stop protobuf; \
	fi
	docker run --name protobuf -d --rm hatlonely/protobuf:1.0.0 tail -f /dev/null
	docker exec protobuf mkdir -p api
	docker cp $< protobuf:/$<
	docker cp rpc-api protobuf:/
	docker exec protobuf bash -c "mkdir -p api/gen/go && mkdir -p api/gen/swagger"
	docker exec protobuf bash -c "protoc -Irpc-api -I. --go_out api/gen/go --go_opt paths=source_relative $<"
	docker exec protobuf bash -c "protoc -Irpc-api -I. --go-grpc_out api/gen/go --go-grpc_opt paths=source_relative $<"
	docker exec protobuf bash -c "protoc -Irpc-api -I. --grpc-gateway_out api/gen/go --grpc-gateway_opt logtostderr=true,paths=source_relative $<"
	docker exec protobuf bash -c "protoc -Irpc-api -I. --openapiv2_out api/gen/swagger --openapiv2_opt logtostderr=true $<"
	docker cp protobuf:api/gen api
	docker stop protobuf
```
