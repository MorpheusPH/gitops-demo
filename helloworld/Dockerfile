# Build the manager binary
FROM golang:1.17 as builder

WORKDIR /workspace

COPY main.go main.go

# Build
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -a -o server main.go

FROM gcr.io/distroless/static:nonroot
WORKDIR /
COPY --from=builder /workspace/server .
USER 65532:65532
EXPOSE 8080

ENTRYPOINT ["/server"]
