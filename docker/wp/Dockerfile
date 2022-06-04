FROM wordpress:latest

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

CMD ["apache2-foreground"]