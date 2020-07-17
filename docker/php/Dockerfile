FROM php:7.4-fpm-alpine

WORKDIR /var/www/html

RUN set -ex \
    && apk --no-cache add \
    postgresql-dev

RUN docker-php-ext-install pdo pdo_pgsql

#Install PHP Extensions (igbinary & memcached)
RUN apk add --no-cache --update libmemcached-libs zlib
RUN set -xe && \
    cd /tmp/ && \
    apk add --no-cache --update --virtual .phpize-deps $PHPIZE_DEPS && \
    apk add --no-cache --update --virtual .memcached-deps zlib-dev libmemcached-dev cyrus-sasl-dev && \
    # Install igbinary (memcached's deps)
    pecl install igbinary && \
    # Install memcached
    ( \
    pecl install --nobuild memcached && \
    cd "$(pecl config-get temp_dir)/memcached" && \
    phpize && \
    ./configure --enable-memcached-igbinary && \
    make -j$(nproc) && \
    make install && \
    cd /tmp/ \
    ) && \
    # Enable PHP extensions
    docker-php-ext-enable igbinary memcached && \
    rm -rf /tmp/* && \
    apk del .memcached-deps .phpize-deps