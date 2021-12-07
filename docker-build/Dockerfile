# From https://github.com/homeport/gonut/tree/master/assets/sample-apps/golang

FROM ghcr.io/shipwright-io/shipwright-samples/golang:1.16 AS build

COPY main.go .
ENV CGO_ENABLED=0
RUN go build \
    -tags netgo \
    -ldflags "-s -w -extldflags '-static'" \
    -o /tmp/helloworld \
    main.go

FROM scratch
COPY --from=build /tmp/helloworld ./helloworld
ENTRYPOINT [ "./helloworld" ]
EXPOSE 8080
