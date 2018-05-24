FROM php:7.2.2-fpm
RUN docker-php-source extract \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo pdo_mysql  \
    && docker-php-source delete

RUN pecl install -o -f redis \
    &&  rm -rf /tmp/pear \
    &&  docker-php-ext-enable redis
RUN pecl install mongodb \
    && docker-php-ext-enable mongodb

CMD ["php-fpm"]
