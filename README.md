# webrpc OpenAPI 3.x (Swagger) generator

## Install webrpc (in development)
```
git clone --single-branch git@github.com:golang-cz/webrpc.git --branch gen_v2_templates_api
cd webrpc
make install
```

## Generate OpenAPI 3.x
```
webrpc-gen -schema=./proto.ridl -target=github.com/golang-cz/webrpc-openapi@v0.1.0 -out openapi.gen.yaml
```

## Run Swagger UI
```
docker run -p 8088:8080 -v $(pwd):/tmp -e SWAGGER_JSON=/tmp/openapi.gen.yaml swaggerapi/swagger-ui
```

http://localhost:8088


### Run Swagger editor
docker run -d -p 80:8080 -v $(pwd):/tmp -e SWAGGER_FILE=/tmp/api.gen.yaml swaggerapi/swagger-editor

