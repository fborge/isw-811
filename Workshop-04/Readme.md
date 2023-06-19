# Habilitando Maquina

## En VMs creamos una nueva carpeta mariadb

mkdir mariadb

Luego iniciamos una nueva maquina 

vagrant init debian/bullseye64

## Editar  y personzalisar ip nueva en Vagrantfile

code Vagrantfile
config.vm.network "private_network", ip: "192.168.33.11"

## Levantamos la nueva maquina
 vagrant up

## Cambiar el nombre de hostname

sudo hostnamectl set-hostname mariadb

Luego salir y volvemos a ingresar

exit 
vagrant ssh

## Actualizar paquetes
sudo apt-get update

## Instalar mariadb-server y mariadb-client

sudo apt-get install mariadb-server mariadb-client

## Cambiar el nombre de hostname

sudo hostnamectl set-hostname database
sudo nano /etc/hosts

## Renombramos el nombre de carpeta mariadb en la maquina anfitriona ubicandonos en VMs

mv mariadb database

## Conectarse a mariadb
En la maquina virtual database ingresamos al motor de base de datos Mariadb, lanzando el comando

sudo mysql

## Crear usuarios y asignar contaseña, crear base de datos para LFTS

create user fran identified by 'secret';
create user laravel identified by 'secret';
create database lfts;
grant all privileges on lfts.* to laravel;
flush privileges;
quit

## Probar ingresar a la base de datos con el usuario laravel

 mysql -u laravel -p

## Mostramos database
