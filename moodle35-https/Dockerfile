FROM moodlehq/moodle-php-apache:7.0

RUN apt-get update
RUN apt-get install -y git

RUN pecl install solr redis igbinary xdebug-2.5.0
RUN docker-php-ext-enable solr redis igbinary xdebug

RUN git clone -b MOODLE_35_STABLE https://github.com/moodle/moodle.git /var/www/html

ADD config.php /var/www/html/config.php

EXPOSE 443

VOLUME /etc/ssl/certs

RUN a2enmod rewrite
RUN a2enmod ssl

ADD site-https.conf /etc/apache2/sites-enabled/

ENV WWWROOT=https://localhost
ENV DBTYPE=mariadb
ENV DBHOST=localhost
ENV DBNAME=moodle
ENV DBUSER=dbuser
ENV DBPASS=123456
ENV DBPORT=3306
ENV DBSOCKET=1
ENV MDLPREFIX=mdl_
ENV LANG=es

CMD ["apache2-foreground"]