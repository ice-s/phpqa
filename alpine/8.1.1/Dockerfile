FROM jakzal/phpqa:1.79.5-php8.1-alpine

RUN docker-php-ext-install sockets

RUN apk update \
    && apk upgrade \
    && apk add --no-cache \
        freetype-dev \
        libpng-dev \
        jpeg-dev \
        libjpeg-turbo-dev \
        imagemagick-dev \
        imagemagick \
        autoconf \
        g++ \
        make \
        pkgconfig
RUN docker-php-ext-install gd
RUN docker-php-ext-install exif
RUN apk add --no-cache php81-pecl-imagick \
    && ln -s /usr/lib/php81/modules/imagick.so /usr/local/lib/php/extensions/no-debug-non-zts-20230831/ \
    && docker-php-ext-enable imagick