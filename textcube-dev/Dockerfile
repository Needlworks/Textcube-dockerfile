
FROM ubuntu:14.04
MAINTAINER Jeongkyu Shin <inureyes@gmail.com>

RUN apt-get update
RUN apt-get install -y \
    git \
    nginx \
    sqlite3 \
    php5-fpm \
    xz-utils
RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf
RUN chown -R www-data:www-data /var/lib/nginx
RUN mkdir /var/www
RUN git clone git@github.com:Needlworks/Textcube.git /var/www/textcube
RUN mkdir /var/www/textcube/attach /var/www/textcube/cache /var/www/textcube/skin/blog/customize /var/www/textcube/data
RUN chown -R www-data:www-data /var/www/textcube/attach /var/www/textcube/cache /var/www/textcube/skin/blog/customize /var/www/textcube/data
COPY config.php /var/www/textcube/config.php
COPY textcube.sqlite /var/www/textcube/data/textcube.sqlite

VOLUME ["/var/www/textcube/data", "/var/www/textcube/skin", "/var/www/textcube/cache", "/var/www/textcube/attach","/var/log/nginx"]

WORKDIR /var/www/textcube

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
