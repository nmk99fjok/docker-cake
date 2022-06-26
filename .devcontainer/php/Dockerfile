FROM php:8.0-fpm

ARG USERNAME=vscode
ARG USER_UID
ARG USER_GID=${USER_UID}

ARG LOCALE=en_US.UTF-8
ARG TIME_ZONE=UTC

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV DEBIAN_FRONTEND=noninteractive
ENV LANG=${LOCALE}
ENV TZ=${TIME_ZONE}

RUN apt-get update \
    && apt-get install -y git locales unzip zip \
    && apt-get install -y libonig-dev libicu-dev \
    && docker-php-ext-install intl pdo_mysql bcmatch \
    #
    #
    && groupadd --gid $USER_GID $USERNAME \
    && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
    #
    #
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME\
    && chmod 0440 /etc/sudoers.d/$USERNAME

COPY --from=composer:2.1 /usr/bin/composer /usr/bin/composer
COPY --from=node:16.12 /usr/local/bin /usr/local/bin