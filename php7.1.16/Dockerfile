FROM php:7.1.16-fpm

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libcurl4-openssl-dev \
        pkg-config \
        libssl-dev

RUN docker-php-source extract \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo pdo_mysql  \
    && docker-php-ext-install ziparchive \
    && docker-php-source delete \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN pecl install redis \
    &&  rm -rf /tmp/pear \
    &&  docker-php-ext-enable redis
RUN pecl install mongodb \
    &&  rm -rf /tmp/pear \
    && docker-php-ext-enable mongodb

RUN pecl install xdebug-2.5.0 \
    &&  rm -rf /tmp/pear \
    && docker-php-ext-enable xdebug
CMD ["php-fpm"]


