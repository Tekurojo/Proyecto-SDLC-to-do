# Proyecto-SDLC-to-do
Actividad en grupo


---------------------------------------------------------|MEDIDAS DE SEGURIDAD PARA LA EJECUACIÓN DE LA APP|--------------------------------------------

Ejecutar tu aplicación Docker sin ser usuario root y con los mínimos privilegios
Para ejecutar tu aplicación Docker sin ser usuario root y con los mínimos privilegios, debes seguir estos pasos:

1. Define un usuario no root:

Crea un usuario no root en tu sistema Docker host que tendrá los permisos necesarios para ejecutar tu aplicación. Puedes hacerlo utilizando el siguiente comando:

Bash
sudo useradd -r -m <nombre-de-usuario>
Usa el código con precaución.
content_copy
Este comando creará un usuario llamado <nombre-de-usuario> con un directorio personal y establecerá los permisos adecuados para que el usuario pueda ejecutar comandos.

2. Crea un grupo para tu aplicación:

Crea un grupo para tu aplicación utilizando el siguiente comando:

sudo groupadd <nombre-de-grupo>
Este comando creará un grupo llamado <nombre-de-grupo>.

3. Agrega el usuario al grupo:

Agrega el usuario que creaste en el paso 1 al grupo que creaste en el paso 2 utilizando el siguiente comando:

Bash
sudo usermod -aG <nombre-de-grupo> <nombre-de-usuario>
Este comando agregará el usuario <nombre-de-usuario> al grupo <nombre-de-grupo>.

4. Establece los permisos de archivo correctos:

Asegúrate de que los archivos de tu aplicación tengan los permisos correctos. No debes otorgar permisos de escritura a ningún archivo que no lo necesite. Puedes utilizar el comando chmod para establecer los permisos de archivo.

5. Ejecuta tu aplicación:

Para ejecutar tu aplicación, puedes utilizar el siguiente comando:

docker run -u <nombre-de-usuario>:<nombre-de-grupo> -d -p <puerto-de-la-aplicacion>:<puerto-de-la-aplicacion> <nombre-de-imagen>
Este comando ejecutará tu aplicación como el usuario <nombre-de-usuario> y el grupo <nombre-de-grupo>. También expondrá el puerto <puerto-de-la-aplicacion> del contenedor al puerto <puerto-de-la-aplicacion> del host.

Ejemplo:

mi-aplicacion, puerto 3000, usuario "dockeruser" y un grupo "app".

Para ejecutar:

docker run -u dockeruser:app -d -p 3000:3000 mi-aplicacion

Beneficios de ejecutar tu aplicación sin ser usuario root:

-Seguridad: Ejecutar tu aplicación sin ser usuario root ayuda a reducir la superficie de ataque y a proteger tu sistema de ataques.
-Aislamiento: Ejecutar tu aplicación en un contenedor aislado ayuda a proteger tu sistema de otros procesos que se ejecutan en el host.
-Portabilidad: Las aplicaciones que se ejecutan en contenedores son más portátiles y se pueden ejecutar en cualquier sistema que tenga Docker instalado.

6. Aislar la red:

Ejecuta la aplicación en una red Docker separada para evitar la comunicación con otras aplicaciones o el host.
Utiliza la opción --network <nombre-de-red> en el comando docker run para especificar la red.
Crea una red personalizada con el comando docker network create <nombre-de-red>.

7. Limitar puertos expuestos:

Expon solo los puertos necesarios para el funcionamiento de la aplicación.
Utiliza la opción -p <puerto-contenedor>:<puerto-host> en el comando docker run para especificar los puertos.
No exponer puertos innecesarios que podrían ser utilizados para ataques.

8. Utilizar la herramienta Snyk para escanear vulnerabilidades en aplicaciones Docker:
Priorizar las vulnerabilidades críticas y toma las medidas necesarias para corregirlas.
Esto puede implicar actualizar dependencias, modificar configuraciones o reemplazar componentes vulnerables.
Snyk proporciona enlaces a recursos y guías para ayudar a resolver las vulnerabilidades.
