FROM php:8.3-fpm

WORKDIR /var/www/app

ARG UID
ARG GID
ARG UNAME

RUN apt-get update && \
    apt-get install --no-install-recommends -y \
    nano unzip zip libxml2-dev sudo nodejs npm && \
    docker-php-ext-install pdo_mysql

# php
RUN apt-get update && apt-get install -y \
    libicu-dev \
    libonig-dev \
    libzip-dev \
    zip \
    unzip \
    git \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install zip
RUN docker-php-ext-enable intl mbstring zip

RUN apt-get update -y && \
    apt-get install -y --no-install-recommends libpq-dev zlib1g-dev libpng-dev libzip-dev mariadb-client

RUN docker-php-ext-install pdo_mysql pcntl gd

# Debugger
RUN pecl install xdebug && docker-php-ext-enable xdebug

RUN groupadd --gid ${GID} ${UNAME} \
    && useradd --home-dir "/home/${UNAME}" --create-home --uid ${UID} \
    --gid ${GID} --shell /bin/bash --skel /dev/null ${UNAME}

RUN echo "${UNAME} ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
RUN usermod -a -G www-data ${UNAME}

COPY --from=composer:2.7.2 /usr/bin/composer /usr/bin/composer

COPY ./app .
COPY ./entrypoint.sh /entrypoint.sh

USER ${UNAME}

ENTRYPOINT ["/entrypoint.sh"]
