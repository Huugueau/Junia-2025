# Utilise l'image officielle MySQL
FROM mysql:8.0

# Variables d'environnement MySQL
ENV MYSQL_ROOT_PASSWORD=C7zqUqB7fKnbzz
ENV MYSQL_DATABASE=croupier

# Copier le fichier SQL dans le container pour l'initialisation
COPY croupier.sql /docker-entrypoint-initdb.d/croupier.sql

# Exposer le port MySQL
EXPOSE 3306
