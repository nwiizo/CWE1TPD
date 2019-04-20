FROM golang:latest as builder

ENV CGO_ENABLED=0
ENV GOOS=linux
ENV GOARCH=amd64
WORKDIR /work
COPY . .
RUN go build main.go

# runtime image
FROM alpine
RUN apk add --no-cache ca-certificates
COPY --from=builder /work /app
RUN ls /app
EXPOSE 80
CMD /app/main
