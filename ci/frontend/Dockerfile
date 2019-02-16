FROM php:5.4-apache

RUN	apt-get update && apt-get upgrade -y
RUN apt-get install -y libpq-dev unzip
RUN docker-php-ext-install pdo pdo_pgsql pgsql
RUN pear channel-update pear.php.net && pear upgrade --force && pear install DB

RUN mkdir /tmp/smarty && cd /tmp/smarty && \
    curl -Lo smarty.zip "https://github.com/smarty-php/smarty/archive/v3.1.33.zip" && \
    unzip smarty.zip && \
    cp -R smarty-3.1.33/libs/* /usr/local/lib/php && \
    cd / && rm -rf /tmp/smarty

RUN echo date.timezone = "Europe/Amsterdam" > $PHP_INI_DIR/conf.d/timezone.ini

EXPOSE 80
