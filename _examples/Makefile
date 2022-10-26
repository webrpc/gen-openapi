.PHONY: all generate diff

all: generate diff

generate:
	webrpc-gen -schema=./proto.ridl -target=../ -out=./openapi.gen.yaml

diff:
	git diff --color --ignore-all-space --ignore-blank-lines --exit-code .