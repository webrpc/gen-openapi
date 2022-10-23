docker run -d -p 80:8080 -v $(pwd):/tmp -e SWAGGER_FILE=/tmp/api.gen.yaml swaggerapi/swagger-editor

webrpc-gen -schema=../webrpc/_examples/golang-basics/example.ridl -target . -out api.gen.yaml