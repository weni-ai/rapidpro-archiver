FROM golang:1.22-alpine3.19

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
