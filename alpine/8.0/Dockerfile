FROM jakzal/phpqa:1.92-php8.0-alpine

RUN docker-php-ext-install sockets

RUN apk update \
    && apk upgrade \
    && apk add --no-cache \
        freetype-dev \
        libpng-dev \
        jpeg-dev \
        libjpeg-turbo-dev
RUN docker-php-ext-install gd