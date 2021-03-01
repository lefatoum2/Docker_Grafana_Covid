# Docker_Grafana_Covid

###Voir tous les conteneurs actifs:
docker ps

###Travailler sur le conteneur mysql en bash:
docker exec -it data1_db_1 bash

###Se connecter à la base de donnée:
mysql -u user -password

###Afficher les bases de donnée créés : 
show databases

### Quelques requêtes:
SELECT max(people_vaccinated)
FROM `db`.`country_vaccinations2`;

# Création de la base de données avec Docker-compose et mysql

## docker-compose.yml 

<blockquote>
version: '3.3'
services:
  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: 'db'
      # So you don't have to use root, but you can if you like
      MYSQL_USER: 'user'
      # You can use whatever password you like
      MYSQL_PASSWORD: 'password'
      # Password for root access
      MYSQL_ROOT_PASSWORD: 'password'
    ports:
      # <Port exposed> : < MySQL Port running inside container>
      - '3306:3306'
    expose:
      # Opens port 3306 on the container
      - '3306'
      # Where our data will be persisted
    volumes:
      - my-db:/var/lib/mysql
# Names our volume
volumes:
  my-db:
</blockquote>
  
  
  
