FROM php:8.1.12-fpm as base

#COPY ./docker/app/docker-php-entrypoint /usr/local/bin/docker-php-entrypoint
#COPY ./docker/app/php.ini /usr/local/etc/php/conf.d/php.ini
RUN #chmod +x /usr/local/bin/docker-php-entrypoint

RUN apt-get update -y && \
    apt-get install -y --no-install-recommends git zip unzip libpq-dev zlib1g-dev libpng-dev libzip-dev mariadb-client

RUN docker-php-ext-install pdo_mysql pcntl gd zip

#COPY ./docker/app/docker.conf /usr/local/etc/php-fpm.d/docker.conf

# Install Composer
RUN #curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www
EXPOSE 9000
