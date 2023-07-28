# First Stage : compile golang to binary
FROM golang:1.20 as build

WORKDIR /app

COPY ["go.mod", "go.sum", "/app/"]

RUN go mod download

COPY . .

RUN go build -o geek-life ./app

# Second Stage : run

FROM ubuntu:23.10

WORKDIR /app

COPY --from=build ./app .

ENTRYPOINT ["./geek-life"]

CMD ["serve"]