Práctica 2 IV
Copyright (C) 2013 Antonio Ángel Guirola Vicente
This program is free software: you can redistribute it and/or
modify
it under the terms of the GNU General Public License as published
by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.
You should have received a copy of the GNU General Public License
along with this program. If not, see <http://www.gnu.
org/licenses/>.

practica2IV
===========

Práctica 2 de la asignatura IV

# Introducción

En esta práctica voy a crear una jaula con una distribución Ubuntu en la que voy a instalar el servidor web Apache así como lo necesario para ejecutar la aplicación de la práctica 1 (PHP, MySQL,...)

# Creación de la jaula

```sh
sudo debootstrap --arch=amd64 quantal /jaulas/quantal/	http://archive.ubuntu.com/ubuntu
sudo apt-get install dchroot
sudo mkdir /var/chroot  
sudo chroot /var/chroot 
sudo nano /etc/schroot/schroot.conf
```

Y añadir:

```sh
[Ubuntu P2IV]
description=Ubuntu
location=/jaulas/quantal
priority=3
users=antonio
groups=sbuild
root-groups=root
```

El siguiente paso es configurar el directorio */proc*:

```sh
sudo mount -o bind /proc jaulas/quantal/proc/
sudo cp /etc/resolv.conf /jaulas/quantal/etc/resolv.conf
```

De esta forma ya podemos acceder a la jaula mediante `sudo chroot /jaulas/quantal`

# Configuración de la jaula

El primer paso es instalar dentro de la jaula el servidor web y los entornos de ejecución necesarios para la aplicación, me he ayudado de [éste tutorial.](http://soportetecnicocurc.blogspot.com.es/2013/03/instalar-apache-php-mysql-y-phpmyadmin.html). Las órdenes son las siguientes:











