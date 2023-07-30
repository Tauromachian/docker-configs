# Use an official PHP runtime as a parent image
FROM localhost/php:8.0-fpm-alpine

# Set working directory
WORKDIR /var/www/html

# Install system dependencies
RUN apk update && apk add --no-cache \
    git \
    icu-dev \
    libzip-dev \
    libpng-dev \
    oniguruma-dev \
    libxml2-utils \
    zip \
    unzip \
    openssl-dev \
    freetype-dev \
    gmp-dev \
    postgresql-dev \
    curl-dev


# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mysqli pdo_pgsql pgsql gd curl fileinfo gmp intl zip
RUN docker-php-ext-enable pdo_mysql mysqli pdo_pgsql pgsql gd curl fileinfo gmp intl zip

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN addgroup -g 1000 composer && adduser -G composer -g composer -s /bin/sh -D composer

# Change ownership of /var/www/html to composer
RUN chown -R composer:composer /var/www/html
ENV COMPOSER_ALLOW_SUPERUSER=1

USER root

