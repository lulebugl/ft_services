FROM alpine:latest

RUN apk update; \
    apk add wget && mkdir /www; \
    apk add php7 php7-fpm php7-opcache php7-gd php7-mysqli php7-zlib php7-curl php7-mbstring php7-json php7-session

RUN wget https://wordpress.org/latest.tar.gz; \
    tar -xvf latest.tar.gz; \
    mv wordpress/* /www; \
    rm -rf /var/cache/apk/*

COPY wp-config.php /www/wp-config.php

RUN mkdir /www/wp-content/uploads

COPY uploads /www/wp-content/uploads

EXPOSE 5050

ENTRYPOINT php -S 0.0.0.0:5050 -t /www/