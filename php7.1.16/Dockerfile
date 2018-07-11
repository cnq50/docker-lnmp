FROM php:7.1.16-fpm

#RUN apt-get update && apt-get install -y \
#        libmongoc-1.0-0 \
#
#RUN docker-php-source extract \
#    && docker-php-ext-install mysqli \
#    && docker-php-ext-install pdo pdo_mysql  \
#    && docker-php-source delete \
#    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
#    && docker-php-ext-install -j$(nproc) gd
#
#RUN pecl install redis \
#    &&  rm -rf /tmp/pear \
#    &&  docker-php-ext-enable redis
#RUN pecl install mongodb \
#    &&  rm -rf /tmp/pear \
#    && docker-php-ext-enable mongodb
#
#RUN pecl install xdebug-2.5.0 \
#    &&  rm -rf /tmp/pear \
#    && docker-php-ext-enable xdebug
#
#CMD ["php-fpm"]


RUN apt-get update
RUN apt-get install -y autoconf pkg-config libssl-dev
RUN pecl install mongodb-1.2.2
RUN docker-php-ext-install bcmath
RUN echo "extension=mongodb.so" >> /usr/local/etc/php/conf.d/mongodb.ini

# Install Laravel dependencies
RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev

RUN docker-php-ext-install iconv mcrypt mbstring \
    && docker-php-ext-install zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

CMD ["php-fpm"]
