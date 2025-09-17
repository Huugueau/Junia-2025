FROM debian:bullseye

# Installer nginx + PHP-FPM + extensions mysql
RUN apt-get update && apt-get install -y \
    nginx \
    php-fpm \
    php-mysql \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Créer le dossier pour le socket PHP-FPM
RUN mkdir -p /run/php

# Supprimer la page par défaut
RUN rm -rf /var/www/html/*

# Copier ton code PHP
COPY ./sources /var/www/html

# Copier la config Nginx
COPY ./nginx.conf /etc/nginx/sites-enabled/default

COPY ./wait-for-it.sh /usr/local/bin/wait-for-it.sh
RUN chmod +x /usr/local/bin/wait-for-it.sh

# Exposer le port 80
EXPOSE 80

# Lancer PHP-FPM et Nginx en foreground
CMD /usr/local/bin/wait-for-it.sh mysql:3306 -- php-fpm7.4 -F & nginx -g "daemon off;"
