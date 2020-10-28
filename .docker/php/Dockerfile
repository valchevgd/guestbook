FROM php:7.4-fpm

LABEL maintainer="Georgi Valchev"

COPY . /web/app/
COPY .docker/php/php.ini /usr/local/etc/php/php.ini

WORKDIR /web/app/

RUN chown -R www-data:www-data /web/app
