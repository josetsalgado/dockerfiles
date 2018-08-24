# Puede ser 5.6, 7.0, 7.1
ARG  PHP_VERSION=5.6
FROM moodlehq/moodle-php-apache:${PHP_VERSION}


RUN apt-get update
RUN apt-get install -y git

RUN pecl install solr redis igbinary xdebug-2.5.0
RUN docker-php-ext-enable solr redis igbinary xdebug

# Moodle branch https://github.com/moodle/moodle
ARG MOODLE_BRANCH=MOODLE_35_STABLE
RUN git clone -b ${MOODLE_BRANCH} https://github.com/moodle/moodle.git /var/www/html

# ADD config.php /var/www/html/config.php

CMD ["apache2-foreground"]