.PHONY: all generate diff

all:
	@echo "make <cmd>:"
	@echo ""
	@echo "commands:"
	@awk -F'[ :]' '/^#+/ {comment=$$0; gsub(/^#+[ ]*/, "", comment)} !/^(_|all:)/ && /^([A-Za-z_-]+):/ && !seen[$$1]++ {printf "  %-24s %s\n", $$1, (comment ? "- " comment : ""); comment=""} !/^#+/ {comment=""}' Makefile

generate:
	SECURITY_SCHEMES="{ \
              'ApiKeyAuth': { \
                'type': 'apiKey', \
                'in': 'header', \
                'description': 'Project access key for authenticating requests', \
                'name': 'X-Access-Key' \
              }, \
              'ServiceAuth': { \
                'type': 'apiKey', \
                'in': 'header', \
                'description': 'Project access key for authenticating requests', \
                'name': 'X-Access-Key' \
              } \
            }"; \
	webrpc-gen \
		-schema=./proto.ridl \
		-target=../ \
		-out=./openapi.gen.yaml \
		-title="Example webrpc API" \
		-apiVersion="v22.11.8"  \
		-serverUrl=https://api.example.com \
		-serverDescription="Production" \
		-securityAnnotation="@auth" \
		-securitySchemes="$$SECURITY_SCHEMES"

diff:
	git diff --color --ignore-all-space --ignore-blank-lines --exit-code .

swagger:
	@echo "Swagger UI is available at http://localhost:8088"
	docker run -p 8088:8080 -v $$(pwd):/docs -e SWAGGER_JSON=/docs/openapi.gen.yaml swaggerapi/swagger-ui
