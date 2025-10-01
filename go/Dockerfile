FROM golang:1.25.1 AS go-file-compiler

WORKDIR /usr/src/app

COPY ./srcs /app ./

COPY /app .

RUN mkdir compiled_sources
RUN go build -ldflags "-s -w" -o compiled_sources/compiled_file helloWorld.go

#ENTRYPOINT [ "go", "build", "-o", "compiled_sources/compiled_file" ]
#CMD [ "helloWorld.go" ]

FROM scratch
WORKDIR /app/compiled_sources
COPY --from=go-file-compiler /usr/src/app/compiled_sources .
ENTRYPOINT [ "./compiled_file" ]