# webrpc OpenAPI 3.x (Swagger) generator

## Generate OpenAPI 3.x YAML file
```
webrpc-gen -schema=./proto.ridl -target=github.com/webrpc/gen-openapi@v0.7.0 -out openapi.gen.yaml
```

### Set custom template variables
Change any of the following default values by passing `-option="Value"` CLI flag to webrpc-gen.

| webrpc-gen -option   | Default value              | Example value              |
|----------------------|----------------------------|----------------------------|
| `-title`             | `{Services[0].Name} API`   | `"Example API"`              |
| `-version`           | `""`                       | `v22.10.25`                |
| `-serverUrl`         | `""`                       | `https://api.example.com`  |
| `-serverDescription` | `""`                       | `"Staging API"`              |

Example:
```
webrpc-gen -schema=./proto.json -target=github.com/webrpc/gen-openapi@v0.7.0 -out openapi.gen.yaml -title="Example webrpc API" -apiVersion="v22.11.8" -serverUrl=https://api.example.com -serverDescription="Production"
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

## Build static html page 
- Use [Redocly](https://redocly.com/docs/redoc/deployment/cli/) tool. There are multiple ways how to use it. 
It can be installed as cli tool via `npx`, `yarn` or `npm` and it can be also used as [Docker image](https://hub.docker.com/r/redocly/redoc/).
- The look and feel of static page can be customized through theming options: https://redocly.com/docs/api-reference-docs/configuration/theming/.

### Build static html file with cli
```
redoc-cli build openapi.gen.yaml
```

### Build static html file with docker
```
docker run --rm -v $(pwd):/api --workdir /api ghcr.io/redocly/redoc/cli build openapi.gen.yaml
```

# Authors
- [golang.cz](https://www.golang.cz)
- [Vojtech Vitek](https://github.com/VojtechVitek)

# License
[MIT LICENSE](./LICENSE)
