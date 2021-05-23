# HLC_06

**-Dominio:** La web es: http://www.moyanoperez.es/alumnos/. Se ha creado el dominio con Hostalia.

**-Características del alojamiento utilizado:** 
		Droplet LEMP Ubuntu 20.04
		Paquete Basic-Premium AMD con 2 GB  Memoria / 1 AMD vCPU  / 50 GB  Disco
		Servidor en Frankfurt 1
		
**-Instrucciones:** 
		Ajustar las DNS del dominio como ya hemos visto en tareas anteriores para que se aloje en el servidor que hemos creado.
		Nos conectamos al servidor con:
		***`ssh root@moyanoperez.es`***
		
Creamos los archivos PHP necesarios (son los de este repositorio)
Subimos los archivos PHP a Github y los descargamos desde el droplet con:

    cd /var/www/html
    sudo wget https://github.com/glaceron/PHP/archive/refs/heads/main.zip
    sudo unzip main.zip
    sudo mv PHP-main alumnos
    sudo chown -R www-data:www-data alumnos

Creamos la base de datos:

    mysql -u root -p < alumnos/data/migracion.sql

Creamos el usuario alumno y le damos permisos para usar la base de datos:

    mysql -u root -p
    mysql> CREATE  USER  'alumno'@'localhost'  IDENTIFIED  BY  'Malaga20*';
    mysql> GRANT  ALL  PRIVILEGES  ON tutorial_crud.* TO  'alumno'@'localhost';

Y accedemos al dominio desde un navegador para comprobar su funcionamiento:
	http://www.moyanoperez.es/alumnos/
