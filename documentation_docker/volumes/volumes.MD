# Support de cours VOLUMES - Docker


Bind volumes


Named volumes
permet la pérsistance des données

peut être "shared" pour être accèdés par plusieurs containers

peut être un "volume docker" qui est gérés par Docker
pour les données que l'ont va jamais toucher


sinion mettre volume dans l'oridnateur avec a "shared" volume, pour pouvoir les modifier


crée volume :

![creation fichier](/creation_volume_pour_db_mysql.png "creation ficher")

docker run -e MYSQL_ROOT_PASSWORD=psw1333 --name mysql-A -d -p 3306:3306 --volume=C:/data/db_data:/var/lib/mysql mysql

PAS OUBLIER DE SE LOGIN

crée une db

mettre une table

insérer une donnée

quitter le container

lancer un nouveau container mysql-B

vérifier que les données sont dans ce container aussi