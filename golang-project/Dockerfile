FROM golang:alpine

WORKDIR /usr/src/app

EXPOSE 8080

COPY go.* .

RUN go mod download

COPY . .

CMD ["go","run","main.go"]
