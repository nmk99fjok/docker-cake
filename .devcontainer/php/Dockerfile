FROM php:8.0-fpm

ARG USERNAME=vscode
ARG USER_UID
ARG USER_GID=${USER_UID}

ARG LOCALE=en_US.UTF-8
ARG TIME_ZONE=UTC

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV DEBIAN_FRONTEND noninteractive
ENV LANG=${LOCALE}
ENV TZ=${TIME_ZONE}

RUN apt-get update \
    && apt-get install -y git locales unzip zip \
    && apt-get install -y libonig-dev libicu-dev \
    && docker-php-ext-install intl pdo_mysql bcmatch