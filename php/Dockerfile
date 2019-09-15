FROM php:7.2-fpm

RUN pecl install redis \
    && pecl install xdebug \
    && docker-php-ext-enable redis xdebug

RUN apt-get update && apt-get install -y \
        curl \
        wget \
        git \
        libxslt-dev \
        libicu-dev \
        libmcrypt-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libwebp-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-webp-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install \
    pdo_mysql \
