# webrpc OpenAPI 3.x (Swagger) generator

## Install webrpc-gen (v0.7.0 development branch)
```
git clone --single-branch git@github.com:golang-cz/webrpc.git --branch templates_v0.7.0
cd webrpc
make install
```

## Generate OpenAPI 3.x YAML file
```
webrpc-gen -schema=./proto.ridl -target=github.com/webrpc/gen-openapi@v0.6.0 -out openapi.gen.yaml
```

### Set custom template variables
Change any of the following default values by passing `-Option="Value"` CLI flag to webrpc-gen.

| Option               | Default value              | Example value              |
|----------------------|----------------------------|----------------------------|
| `-Title`             | `{Services[0].Name} API`   | `"Example API"`              |
| `-Version`           | `""`                       | `v22.10.25`                |
| `-ServerUrl`         | `""`                       | `https://api.example.com`  |
| `-ServerDescription` | `""`                       | `"Staging API"`              |

Example:
```
webrpc-gen -schema=./proto.json -target=github.com/webrpc/gen-openapi@v0.6.0 -out openapi.gen.yaml -Title="My Own Title"
```

## Open documentation in Swagger UI
```
docker run -p 8088:8080 -v $(pwd):/tmp -e SWAGGER_JSON=/tmp/openapi.gen.yaml swaggerapi/swagger-ui
```

http://localhost:8088

### Open documentation in Swagger editor
```
docker run -p 8088:8080 -v $(pwd):/tmp -e SWAGGER_FILE=/tmp/openapi.gen.yaml swaggerapi/swagger-editor
```

http://localhost:8088

# Authors
- [golang.cz](https://www.golang.cz)
- [Vojtech Vitek](https://github.com/VojtechVitek)

# License
[MIT](./LICENSE)
