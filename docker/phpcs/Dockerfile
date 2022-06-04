FROM php:7.4.29-fpm

RUN apt-get update && apt-get install -y git

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN composer global require squizlabs/php_codesniffer

RUN COMPOSER_HOME="/composer" composer global require --prefer-dist --no-progress --dev squizlabs/php_codesniffer
RUN git clone -b master https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards.git /composer/vendor/squizlabs/php_codesniffer/Standards/WordPress

ENV PATH=/composer/vendor/bin:$PATH

RUN phpcs --config-set installed_paths /composer/vendor/squizlabs/php_codesniffer/Standards/WordPress && phpcs --config-set default_standard WordPress

WORKDIR /app

CMD ["phpcs"]