FROM alpine:latest

RUN echo '@edgetesting http://dl-cdn.alpinelinux.org/alpine/edge/testing' >> /etc/apk/repositories \
 && apk update \
 && apk add pptpclient@edgetesting

COPY ["entrypoint.sh", "/"]

CMD ["/entrypoint.sh"]
