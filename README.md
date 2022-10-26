# webrpc OpenAPI 3.x (Swagger) generator

## Install webrpc (v0.7.0 development branch)
```
git clone --single-branch git@github.com:golang-cz/webrpc.git --branch gen_v2_templates_api
cd webrpc
make install
```

## Generate OpenAPI 3.x documentation
```
webrpc-gen -schema=./proto.ridl -target=github.com/webrpc/gen-openapi@v0.6.0 -out openapi.gen.yaml
```

## CLI options
Change any of the following values by passing `-Option="Value"` in the webrpc-gen CLI.

| Option             | Default value              | Example value              |
|--------------------|----------------------------|----------------------------|
| -Title             | `{Services[0].Name} API`   | `Example API`              |
| -Version           | `""`                       | `v22.10.25`                |
| -ServerUrl         | `""`                       | `https://api.example.com`  |
| -ServerDescription | `""`                       | `Staging API`              |

## Open in Swagger UI
```
docker run -p 8088:8080 -v $(pwd):/tmp -e SWAGGER_JSON=/tmp/openapi.gen.yaml swaggerapi/swagger-ui
```

http://localhost:8088

### Open in Swagger editor
```
docker run -p 8088:8080 -v $(pwd):/tmp -e SWAGGER_FILE=/tmp/openapi.gen.yaml swaggerapi/swagger-editor
```

http://localhost:8088

# Authors
- [golang.cz](https://www.golang.cz)
- [Vojtech Vitek](https://github.com/VojtechVitek)

# License
- MIT
