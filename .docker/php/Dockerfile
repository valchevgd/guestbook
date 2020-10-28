FROM php:7.4-fpm

LABEL maintainer="Georgi Valchev"

# Install PHP Composer
RUN apt-get -yqq update \
    && apt-get -yqq install --no-install-recommends unzip \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony/bin/symfony /usr/local/bin/symfony

COPY . /web/app/
COPY .docker/php/php.ini /usr/local/etc/php/php.ini

WORKDIR /web/app/

RUN chown -R www-data:www-data /web/app
