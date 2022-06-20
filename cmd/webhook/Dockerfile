FROM golang:1.18 AS build

ENV GOOS=linux
ENV GOARCH=amd64
ENV CGO_ENABLED=0

WORKDIR /app
COPY . /app

RUN go build -o bin/webhook .

#---

FROM scratch AS run

COPY --from=build /app/bin/webhook /usr/local/bin/

CMD ["webhook"]