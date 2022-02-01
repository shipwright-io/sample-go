# From https://github.com/homeport/gonut/tree/master/assets/sample-apps/golang

# Must be set to 1.16
ARG GO_VERSION

FROM ghcr.io/shipwright-io/shipwright-samples/golang:${GO_VERSION} AS build

# Must be set to main.go
ARG MAIN

COPY "${MAIN}" .
ENV CGO_ENABLED=0
RUN go build \
    -tags netgo \
    -ldflags "-s -w -extldflags '-static'" \
    -o /tmp/helloworld \
    "${MAIN}"

FROM scratch
COPY --from=build /tmp/helloworld ./helloworld
ENTRYPOINT [ "./helloworld" ]
EXPOSE 8080
