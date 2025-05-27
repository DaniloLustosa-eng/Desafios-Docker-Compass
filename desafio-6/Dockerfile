FROM golang:1.23 AS builder

WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o /app/app

FROM alpine:latest
COPY --from=builder /app/app /app
EXPOSE 8080
USER nonroot:nonroot
ENTRYPOINT ["/app"]



