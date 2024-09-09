# Support de cours - Docker

P_Docker 347 - Nima Zarrabi - CID3A

# Introduction

Check Docker version¨

![login_docker](./doc_media/get_docker_version.png "img_1")

Log in Docker

![login_docker](./doc_media/login_docker.png "img_2")

Pull image

![login_docker](./doc_media/pull_image.png.png "img_3")

Run from image

![login_docker](./doc_media/run_from_image.png "img_4")

List containers

![login_docker](./doc_media/list_running_containers_and_list_all_containers.png "img_5")

List image

![login_docker](./doc_media/list_images.png "img_6")

Stop specific image

![login_docker](./doc_media/stop_specific_container.png "img_7")

Stop and remove container

![login_docker](./doc_media/stop_and_remove_container.png "img_8")

List container ID

![login_docker](./doc_media/list_containers_id.png "img_9")

Erased all unused data

![login_docker](./doc_media/erase_all_unused_data.png "img_10")

Erase all data

![login_docker](./doc_media/erase_all_data.png "img_11")

Stop andremove container interactive

![login_docker](./doc_media/stop_and_remove_container_interactive.png "img_12")

Stop specif

![login_docker](./doc_media/stop_specific_container.png "img_13")

update

apt update

![login_docker](./doc_media/apt_update.png "img_14")

apt update from cmd

![login_docker](./doc_media/apt_update_from_cmd.png "img_15")

upgrade

apt upgrade

![login_docker](./doc_media/apt_upgrade.png "img_16")

apt upgrade from cmd

![login_docker](./doc_media/apt_upgrade_from_cmd.png "img_17")

check ubuntu name

![login_docker](./doc_media/check_ubuntu_name.png "img_18")

list releases from ubuntu terminal

![login_docker](./doc_media/enter_ubuntu_terminal_and_list_releases.png "img_19")

go in ubuntu bash

![login_docker](./doc_media/enter_ubunu_bash.png "img_20")

executer une commande ubuntu directement 

![login_docker](./doc_media/execute_ubuntu_command_directly.png "img_21")


et finalement, pour quitter ubuntu

![login_docker](./doc_media/exit_ubuntu.png "img_22")

Installer une app dans ubuntu

![login_docker](./doc_media/install_nano.png "img_23")

Installer un zip dans ubuntu depuis le cmd

![login_docker](./doc_media/install_zip_ubuntu_from_cmd.png "img_24")

List les fichiers dans ubuntu

![login_docker](./doc_media/list_files_ubuntu.png "img_25")

List des fichiers specifics dans ubuntu

![login_docker](./doc_media/list_specific_file_ubuntu.png "img_26")

Transferer un fichier zip à ubuntu

![login_docker](./doc_media/transfer_compressed_file_to_ubuntu.png "img_27")


DTI 

d = detachable

T = 

I = interactive

![login_docker](./doc_media/login_docker.png "img_10")

docker rm for remove


cat = read file


-y pour "yes" par défault

nano = editeur de text

exec execute depuis la root de la machine

--force pour TOUT erase


myql 3306:3306
port itnerieur / exterieur

# Volumes


Bind volumes


Named volumes
permet la pérsistance des données

peut être "shared" pour être accèdés par plusieurs containers

peut être un "volume docker" qui est gérés par Docker
pour les données que l'ont va jamais toucher


sinion mettre volume dans l'oridnateur avec a "shared" volume, pour pouvoir les modifier


crée volume :

![creation fichier](./doc_media/creation_volume_pour_db_mysql.png "creation ficher")

docker run -e MYSQL_ROOT_PASSWORD=psw1333 --name mysql-A -d -p 3306:3306 --volume=C:/data/db_data:/var/lib/mysql mysql

PAS OUBLIER DE SE LOGIN

Crée une db

![ creation db](./doc_media/create_db.png "img_29")

mettre une table

![login_docker](./doc_media/create_table.png "img_28")

insérer une donnée

![login_docker](./doc_media/insert_into_table.png "img_28")

Lecture d'une donnée dans la base de données

![login_docker](./doc_media/read_data_in_db.png "img_28")

quitter le container

![login_docker](./doc_media/exit_db_and_stop_container.png "img_28")

lancer un nouveau container mysql-B

![login_docker](./doc_media/log_into_second_msql_container.png "img_28")

vérifier que les données sont dans ce container aussi

![login_docker](./doc_media/read_data_in_db.png "img_28")


# reseau: docker

application (ex: wordpress) à besoin d'une connexion et aussi besoin de communiquer à un service (ex: databaser)

BRIDGE
machine Window
autour du Docker engine
autour du Réseau (NAT)
qui contient les containers
les containers peuvent contacter l'hôte (Windows) grâce à un Reseau BRIDGE

crée reseau : 

docker network create --driver bridge mon-reseau

![create_reseau](./doc_media/creation_reseau.png "reseau")

Docker s'occupe de créer l'ip pour les containers
pas besoin de connaitre l'ip car Docker gère les IP donc seulement besoin de donner le nom des containers

docker run -dit --name container1 --network mon-reseau alpine sh

docker run -dit --name container2 --network mon-reseau alpine sh

docker exec container1 ping -c 4 container2

![ping_reseau](./doc_media/create_multiple_container_and_ping.png "reseau_ping")


HÔTE

machine Window
autour du Docker engine
qui contient les containers
les containers peuvent contacter l'hôte (Windows) sans passé par un Reseau Bridge

OVERLAY

??????

pull apache 

https://hub.docker.com/_/httpd

``docker pull httpd``

usr/local/apache2/htdocs/

docker run -dit -httpd --name apache-A -p 8080:80 -v C:/data/html:/usr/local/apache/htdocs/ httpd:2.4

PHP

docker run -it --rm --name PHP-A -v C:/data/php:/usr/src/myapp -w /usr/src/myapp php:8.2-cli php index.php

![ link rep to other rep ](./doc_media/link_default_apache_rep_to_set_rep.png " rep_link")

docker stats

![stats](./doc_media/docker_stats.png "docker_stats")


docker logs

![logs](./doc_media/docker_logs.png "docker_logs")


CPU limits

![cpus](./doc_media/options_cpus.png "options_cpus")


--cpus=<value>	Specify how much of the available CPU resources a container can use. For instance, if the host machine has two CPUs and you set --cpus="1.5", the container is guaranteed at most one and a half of the CPUs. This is the equivalent of setting --cpu-period="100000" and --cpu-quota="150000"



# Dockerfile

3 etapes essensiels 

fichier                     registry      service
Dockerfile -> BUILD -> Creation d'image -> RUN

ne pas mettre plusieurs RUN dans dockerfile car il fonctionne en couches et le moins de couches le plus léger l'image

# Push une image dans dockerhub

Push sa propre image sur docker hub
attention de se login avant !!

docker build . -t nimaetml/my-go-app:1.0

![build for docker hub](./doc_media/build_docker_image_to_push.png)

docker push nimaetml/my-go-app:1.0

![push to docker hub](./doc_media/push_docker_image_to_dockerhub.png)