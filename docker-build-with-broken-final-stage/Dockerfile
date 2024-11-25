# From https://github.com/homeport/gonut/tree/master/assets/sample-apps/golang

FROM ghcr.io/shipwright-io/shipwright-samples/golang:1.18 AS build

COPY main.go .
ENV CGO_ENABLED=0
RUN go build \
    -ldflags "-s -w -extldflags '-static'" \
    -o /tmp/helloworld \
    main.go

FROM scratch AS working-final
COPY --from=build /tmp/helloworld ./helloworld
ENTRYPOINT [ "./helloworld" ]
EXPOSE 8080

# the following stage is INTENTIONALLY broken, one can only have a successful run when specifying working-final as target stage
FROM scratch
RUN non-existing-command
