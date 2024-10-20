FROM alpine:latest

RUN apk update 
RUN apk add --no-cache \
    lua5.3 \
    lua5.3-dev \
    luarocks5.3 \
    gcc \
    musl-dev \
    postgresql \
    postgresql-dev \
    curl-dev


# Lua dependencies
RUN luarocks-5.3 install luasocket
RUN luarocks-5.3 install luasql-postgres PGSQL_INCDIR=/usr/include/postgresql

WORKDIR /app
