FROM php:7.4-fpm-alpine

LABEL maintainer="Georgi Valchev"

# Install Additional dependencies
RUN apk update && apk add --no-cache $PHPIZE_DEPS \
    build-base vim curl gcc git bash tzdata \
    php7 \
    php7-fpm \
    php7-common \
    php7-pdo_mysql \
    php7-mysqli \
    php7-mcrypt \
    php7-mbstring \
    php7-xml \
    php7-openssl \
    php7-json \
    php7-phar \
    php7-zip \
    php7-gd \
    php7-dom \
    php7-session \
    php7-zlib \
    postgresql-dev \
    libxslt-dev \
    libzip-dev \
    libpng-dev \
    rabbitmq-c rabbitmq-c-dev

RUN pecl install redis amqp

# Install extensions
RUN docker-php-ext-install bcmath pdo pdo_mysql pcntl sockets pdo_pgsql intl xsl zip gd
RUN docker-php-ext-enable redis amqp

# Install PHP Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#Install Symfony CLI
RUN curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony/bin/symfony /usr/local/bin/symfony

COPY . /web/app/
COPY .docker/php/php.ini /usr/local/etc/php/php.ini

WORKDIR /web/app/

RUN chown -R www-data:www-data /web/app
