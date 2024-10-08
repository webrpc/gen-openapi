.PHONY: all generate diff

all: generate diff

generate:
	SECURITY_SCHEMES="{ \
              'ApiKeyAuth': { \
                'type': 'apiKey', \
                'in': 'header', \
                'description': 'Project access key for authenticating requests, get an access key at https://sequence.build', \
                'name': 'X-Access-Key' \
              }, \
              'ServiceAuth': { \
                'type': 'apiKey', \
                'in': 'header', \
                'description': 'Project access key for authenticating requests, get an access key at https://sequence.build', \
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
