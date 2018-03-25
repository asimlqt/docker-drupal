FROM asimlqt/php-apache:7.1-dev

COPY ./vhost.conf /etc/apache2/sites-available/000-default.conf

RUN apt-get install -y --no-install-recommends mysql-client