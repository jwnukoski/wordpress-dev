FROM wordpress:latest
RUN apt update
RUN pecl install xdebug

COPY ./conf.d/xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
COPY ./conf.d/error_reporting.ini /usr/local/etc/php/conf.d/error_reporting.ini
COPY ./php.ini /usr/local/etc/php/php.ini
