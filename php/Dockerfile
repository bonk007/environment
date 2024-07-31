FROM php:8.3-cli-alpine3.20

WORKDIR /app

RUN apk add --no-cache --update supervisor curl-dev oniguruma-dev libpq-dev libxml2-dev icu-dev libzip-dev pcre-dev ${PHPIZE_DEPS}

RUN docker-php-ext-install bcmath curl exif intl mbstring mysqli opcache pdo pdo_mysql pdo_pgsql pgsql xml zip

RUN pecl install -o -f redis swoole

RUN docker-php-ext-enable redis swoole

COPY 00-custom.ini /usr/local/etc/php/conf.d/00-custom.ini

RUN apk del pcre-dev ${PHPIZE_DEPS} && rm -rf /tmp/pear /var/cache/apk/*
