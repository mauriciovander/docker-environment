FROM php:7-fpm
MAINTAINER mauriciovander@gmail.com
RUN apt-get update && apt-get upgrade -y && apt-get autoremove -y \
    && apt-get install -y nano libmcrypt-dev libpng12-dev libjpeg-dev libpq-dev mysql-client curl \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
    && docker-php-ext-install mcrypt gd mbstring pdo pdo_mysql zip \
    && pecl install xdebug \
    && pecl install mongodb \
    && rm -rf /tmp/pear
ADD ./php.ini /usr/local/etc/php/
ADD ./xdebug.ini /usr/local/etc/php/conf.d
RUN echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)\n" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN mkdir -p /var/www/html/info
ADD ./index.php /var/www/html/info
EXPOSE 9000
