.PHONY: all generate diff

all: generate diff

generate:
	webrpc-gen -schema=./proto.ridl -target=../ -out=./openapi.gen.yaml -title="Example webrpc API" -apiVersion="v22.11.8" -serverUrl=https://api.example.com -serverDescription="Production"

diff:
	git diff --color --ignore-all-space --ignore-blank-lines --exit-code .
