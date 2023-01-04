# webrpc OpenAPI 3.x (Swagger) generator  <!-- omit in toc -->

This repo contains the templates used by the [webrpc-gen](https://github.com/webrpc/webrpc) cli to code-generate OpenAPI documentation from webrpc schema.

- [Generate OpenAPI 3.x YAML file](#generate-openapi-3x-yaml-file)
  - [Set custom template variables](#set-custom-template-variables)
- [Open in Swagger UI](#open-in-swagger-ui)
- [Build static HTML documentation](#build-static-html-documentation)
- [Authors](#authors)
- [License](#license)

# Generate OpenAPI 3.x YAML file
```
webrpc-gen -schema=./proto.ridl -target=github.com/webrpc/gen-openapi@v0.7.0 -out petstore.gen.yaml
```

## Set custom template variables
Change any of the following default values by passing `-option="Value"` CLI flag to webrpc-gen.

| webrpc-gen -option   | Default value              | Example value              |
|----------------------|----------------------------|----------------------------|
| `-title`             | `{Services[0].Name} API`   | `"Example API"`              |
| `-version`           | `""`                       | `v22.10.25`                |
| `-serverUrl`         | `""`                       | `https://api.example.com`  |
| `-serverDescription` | `""`                       | `"Staging API"`              |

Example:
```
webrpc-gen -schema=./petstore.ridl -target=github.com/webrpc/gen-openapi@v0.7.0 -out petstore.gen.yaml -title="Example webrpc API" -apiVersion="v22.11.8" -serverUrl=https://api.example.com -serverDescription="Production"
```

# Open in Swagger UI

Open generated documentation in Swagger editor:
```
docker run -p 8088:8080 -v $(pwd):/app -e SWAGGER_JSON=/app/petstore.gen.yaml swaggerapi/swagger-ui
```

Or in Swagger editor:
```
docker run -p 8088:8080 -v $(pwd):/app -e SWAGGER_FILE=/app/petstore.gen.yaml swaggerapi/swagger-editor
```

And go to http://localhost:8088

# Build static HTML documentation
- Use [Redocly](https://redocly.com/docs/redoc/deployment/cli/) tool. There are multiple ways how to use it. 
It can be installed as cli tool via `npx`, `yarn` or `npm` and it can be also used as [Docker image](https://hub.docker.com/r/redocly/redoc/).
- The look and feel of static page can be customized through theming options: https://redocly.com/docs/api-reference-docs/configuration/theming/.

Example:
```
docker run --rm -v $(pwd):/app -w /app ghcr.io/redocly/redoc/cli build petstore.gen.yaml
```

# Authors
- [golang.cz](https://www.golang.cz)
- [Vojtech Vitek](https://github.com/VojtechVitek)

# License
[MIT LICENSE](./LICENSE)
