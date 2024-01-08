FROM jakzal/phpqa:1.79.5-php8.1-alpine

RUN docker-php-ext-install sockets

RUN apk update \
    && apk upgrade \
    && apk add --no-cache \
        freetype-dev \
        libpng-dev \
        jpeg-dev \
        libjpeg-turbo-dev
RUN docker-php-ext-install gd
RUN docker-php-ext-install exif
