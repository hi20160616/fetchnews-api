# fetchnews-api
The api for fetchnews web crawler

# 1. Usage
1. Clone this repo to your go src as `<your go path>/src/github.com/hi20160616/fetchnews-api`
2. Add proto file like https://github.com/hi20160616/ms-bbc/api/fetchnews/bbc/v1/fetchnews.proto
3. Download google proto files by 2.2 and generate code by 2.3

# 2. gRPC

## 2.1. grpc-gateway
Refer:  
https://github.com/grpc-ecosystem/grpc-gateway  
https://grpc-ecosystem.github.io/grpc-gateway/docs/tutorials/introduction/  
https://www.cnblogs.com/FireworksEasyCool/p/12782137.html  

## 2.2. fix import "google/api/annotations.proto"  error
### Copy google/api/annotations.proto and google/api/http.proto
Refer:  
https://github.com/grpc-ecosystem/grpc-gateway/issues/1935  
```
mkdir -p google/api
wget https://raw.githubusercontent.com/googleapis/googleapis/master/google/api/annotations.proto -O google/api/annotations.proto
wget https://raw.githubusercontent.com/googleapis/googleapis/master/google/api/http.proto -O google/api/http.proto
```
## 2.3. Generate
```
protoc --go_out=. --go_opt=paths=source_relative \
    --go-grpc_out=. --go-grpc_opt=paths=source_relative \
    --grpc-gateway_out="../" \
    proto/v1/fetchnews.proto
go mod tidy
```

