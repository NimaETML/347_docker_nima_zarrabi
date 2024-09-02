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

![create_reseau](/creation_reseau.png "reseau")

Docker s'occupe de créer l'ip pour les containers
pas besoin de connaitre l'ip car Docker gère les IP donc seulement besoin de donner le nom des containers

docker run -dit --name container1 --network mon-reseau alpine sh

docker run -dit --name container2 --network mon-reseau alpine sh

docker exec container1 ping -c 4 container2

![ping_reseau](/create_multiple_container_and_ping.png "reseau_ping")


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


docker stats

![stats](/docker_stats.png "docker_stats")


docker logs

![logs](/docker_logs.png "docker_logs")


CPU limits

![cpus](/options_cpus.png "options_cpus")


--cpus=<value>	Specify how much of the available CPU resources a container can use. For instance, if the host machine has two CPUs and you set --cpus="1.5", the container is guaranteed at most one and a half of the CPUs. This is the equivalent of setting --cpu-period="100000" and --cpu-quota="150000"