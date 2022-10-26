.PHONY: all generate diff

all: generate diff

generate:
	webrpc-gen -schema=./proto.ridl -target=../ -out=./openapi.gen.yaml -Title="Example webrpc API" -Version="v20.10.3" -ServerUrl=https://api.example.com -ServerDescription="Production"

diff:
	git diff --color --ignore-all-space --ignore-blank-lines --exit-code .
