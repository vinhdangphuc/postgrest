FROM alpine:latest

ARG POSTGREST_VERSION="v8.0.0"
ARG FILENAME="postgrest-${POSTGREST_VERSION}-linux-x64-static.tar.xz"

ADD https://github.com/PostgREST/postgrest/releases/download/${POSTGREST_VERSION}/${FILENAME} .
ADD ./postgrest.conf /etc/postgrest.conf

RUN apk add --no-cache \
	--virtual .build-deps \
	xz && \
    tar -xf ${FILENAME} && \
    mv postgrest /usr/bin/postgrest && \
    rm -rf ${FILENAME} && \
    apk del .build-deps

CMD ["postgrest", "/etc/postgrest.conf"]

EXPOSE 3000
