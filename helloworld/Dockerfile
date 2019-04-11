FROM gliderlabs/alpine:3.6

RUN apk --no-cache add tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apk del tzdata

WORKDIR /app

COPY api /app

ADD https://github.com/golang/go/raw/master/lib/time/zoneinfo.zip /go/lib/time/zoneinfo.zip

RUN adduser -S gopher && \
    chown -R gopher /go

USER gopher
env GOROOT /go

ENTRYPOINT ["/app/api"]
