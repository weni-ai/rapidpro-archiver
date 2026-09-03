FROM golang:1.23-alpine3.20

WORKDIR /app

RUN apk update \
  && apk add --no-cache --virtual build-deps build-base git postgresql-dev \
  && rm -rf /var/cache/apk/*

RUN addgroup -S golang \
  && adduser -S -G golang golang

COPY . .

RUN go install -v ./cmd/...
RUN chown -R golang /app

USER golang

EXPOSE 8080
ENTRYPOINT ["rp-archiver"]
