FROM php:8.3-fpm

WORKDIR /var/www/app

ARG UID
ARG GID
ARG UNAME

RUN apt-get update && \
    apt-get install --no-install-recommends -y \
    nano unzip zip libxml2-dev sudo nodejs npm && \
    docker-php-ext-install pdo_mysql

# Debugger
RUN pecl install xdebug && docker-php-ext-enable xdebug

RUN groupadd --gid ${GID} ${UNAME} \
    && useradd --home-dir "/home/${UNAME}" --create-home --uid ${UID} \
    --gid ${GID} --shell /bin/bash --skel /dev/null ${UNAME}

RUN echo "${UNAME} ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
RUN usermod -a -G www-data ${UNAME}

COPY --from=composer:2.7.2 /usr/bin/composer /usr/bin/composer

USER ${UNAME}