																¡ATENCION!
-El nuevo contenido de esta carpeta consta de:
	-DockerfileSimulacionError: Este fichero contiene parametros para provocar [Warnings] nuevos durante el analisis de la aplicación "To-do".
	-Reporte1: Este fichero contiene el analisis de Docker Bench Security de la imagen buena de docker.
	-Reporte2: Este fichero contiene el analisis de Docker Bench Security de la imagen "modificada" de docker.
	-Readme.md: Este documento contiene el analisis con las DESCRIPCIONES de los [Warnings] de la imagen BUENA de docker y de la imagen MODIFICADA.
	-Tutorial: Como instalar paso a paso la herramienta "Docker Bench Security" en Linux.


### Paso 1: Instalar Docker Bench Security
1. Clonar el repositorio de Docker Bench Security.
    ```bash
    git clone https://github.com/docker/docker-bench-security.git
    ```

2. Cambiar al directorio del proyecto clonado.
    ```bash
    cd docker-bench-security
    ```

3. Dar permisos de ejecución al script.
    ```bash
    chmod +x docker-bench-security.sh
    ```

### Paso 2: Ejecutar Docker Bench Security
Ejecuta el script para comenzar la auditoría de seguridad.
```bash
sudo ./docker-bench-security.sh
```

El script revisará la configuración de Docker según las recomendaciones del Center for Internet Security (CIS) y te proporcionará un informe detallado sobre posibles vulnerabilidades y mejoras de configuración.

### Paso 3: Interpretar los resultados
Después de ejecutar el script, verás una salida detallada con varias verificaciones y sus resultados. Cada verificación vendrá con una descripción y un estado que puede ser `PASS`, `WARN`, o `INFO`. Revisa estos resultados y ajusta tu configuración de Docker según las recomendaciones.




---------------------------------------Resultados-del-analisis-de-verificación-de-la-aplicación-sin-modificar-parametros:---------------------------------------------

1. Linux Hosts Specific Configuration

    [WARN] 1.1.1 - Ensure a separate partition for containers has been created (Automated)
        Peligro: No tener una partición separada para los contenedores puede llevar a problemas de rendimiento y seguridad. Si un contenedor consume todo el espacio en disco, puede afectar al sistema operativo anfitrión y a otros contenedores.

    [WARN] 1.1.3 - Ensure auditing is configured for the Docker daemon (Automated)
        Peligro: No tener configurada la auditoría para el daemon de Docker puede dificultar la detección de actividades sospechosas o no autorizadas.

    [WARN] 1.1.4 - Ensure auditing is configured for Docker files and directories - /run/containerd (Automated)
        Peligro: Sin auditoría, no se pueden detectar modificaciones no autorizadas ni accesos indebidos a estos archivos críticos.

    [WARN] 1.1.5 - Ensure auditing is configured for Docker files and directories - /var/lib/docker (Automated)
        Peligro: La falta de auditoría en este directorio puede permitir que actividades maliciosas pasen desapercibidas.

    [WARN] 1.1.6 - Ensure auditing is configured for Docker files and directories - /etc/docker (Automated)
        Peligro: Este directorio contiene configuraciones críticas de Docker. Sin auditoría, los cambios no autorizados no se detectarán.

    [WARN] 1.1.7 - Ensure auditing is configured for Docker files and directories - docker.service (Automated)
        Peligro: La auditoría del servicio de Docker es crucial para detectar cambios en cómo se inicia y se gestiona Docker.

    [WARN] 1.1.9 - Ensure auditing is configured for Docker files and directories - docker.socket (Automated)
        Peligro: La auditoría del socket de Docker es importante para detectar accesos no autorizados.

    [WARN] 1.1.10 - Ensure auditing is configured for Docker files and directories - /etc/default/docker (Automated)
        Peligro: Este archivo contiene configuraciones predeterminadas para Docker. Sin auditoría, los cambios pueden comprometer la seguridad.

    [WARN] 1.1.11 - Ensure auditing is configured for Dockerfiles and directories - /etc/docker/daemon.json (Automated)
        Peligro: Este archivo contiene configuraciones del daemon de Docker. La falta de auditoría puede permitir configuraciones inseguras.

    [WARN] 1.1.12 - Ensure auditing is configured for Dockerfiles and directories - /usr/bin/docker-containerd (Automated)
        Peligro: La auditoría de este archivo binario es esencial para garantizar que no haya sido comprometido.

    [WARN] 1.1.13 - Ensure auditing is configured for Dockerfiles and directories - /usr/bin/docker-runc (Automated)
        Peligro: Similar al anterior, este archivo binario necesita auditoría para evitar compromisos de seguridad.

1.2 General Host Configuration

    [WARN] 1.2.1 - Ensure a separate partition for containers has been created (Automated)
        Peligro: Repetido del punto 1.1.1.

2. Docker Daemon Configuration

    [WARN] 2.1 - Ensure network traffic is restricted between containers on the default bridge (Automated)
        Peligro: Sin restricción del tráfico, los contenedores pueden comunicarse libremente, lo que puede facilitar la propagación de ataques.

    [WARN] 2.2 - Ensure the logging level is set to 'info' (Automated)
        Peligro: Configuraciones de logging menos detalladas pueden dificultar la detección y resolución de problemas.

    [WARN] 2.6 - Ensure that the --authorization-plugin parameter is not set to allow all (Manual)
        Peligro: Permitir que cualquier acción sea autorizada puede comprometer seriamente la seguridad del sistema.

3. Docker Daemon Configuration Files

    [WARN] 3.1 - Ensure that the Docker daemon's configuration file ownership is set to root:root (Automated)
        Peligro: Si el archivo de configuración no está protegido, puede ser modificado por usuarios no autorizados.

4. Container Images and Build Files

    [WARN] 4.1 - Ensure that a user for the container has been created (Automated)
        Peligro: Ejecutar contenedores como root puede aumentar los riesgos de seguridad en caso de compromiso.

5. Container Runtime

    [WARN] 5.1 - Ensure that, if applicable, an AppArmor profile is enabled (Automated)
        Peligro: Sin AppArmor, los contenedores tienen menos restricciones de seguridad.

    [WARN] 5.2 - Ensure that, if applicable, SELinux security options are set (Automated)
        Peligro: Similar a AppArmor, SELinux proporciona controles de seguridad adicionales que son importantes.

    [WARN] 5.9 - Ensure that the host's network namespace is not shared (Automated)
        Peligro: Compartir el namespace de red del anfitrión puede exponer el sistema a ataques desde los contenedores.

6. Docker Security Operations

    [WARN] 6.1 - Ensure that image sprawl is avoided (Manual)
        Peligro: Tener demasiadas imágenes puede dificultar la gestión y aumentar los riesgos de seguridad.

    [WARN] 6.2 - Ensure that container sprawl is avoided (Manual)
        Peligro: Similar al anterior, demasiados contenedores pueden ser difíciles de gestionar y asegurar.
        
---------------------------------------Resultados-del-analisis-de-verificación-de-la-aplicación-con-parámetros-MODIFICADOS [ANTES] y [AHORA]---------------------------------------------

    [WARN] 4.1 - Ensure that a user for the container has been created (Automated):
        Antes: [WARN] * Running as root: sad_lehmann
        Ahora: [WARN] * Running as root: flamboyant_morse

    [WARN] 4.6 - Ensure that HEALTHCHECK instructions have been added to container images (Automated):
        Antes: [WARN] * No Healthcheck found: [getting-started-app:latest]
        Ahora: [WARN] * No Healthcheck found: [getting-started-app:latest]
        [WARN] * No Healthcheck found: e346052bbd7e

    [WARN] 5.3 - Ensure that, if applicable, SELinux security options are set (Automated):
        Antes: [WARN] * No SecurityOptions Found: sad_lehmann
        Ahora: [WARN] * No SecurityOptions Found: flamboyant_morse

    [WARN] 5.9 - Ensure that only needed ports are open on the container (Manual):
        Antes: [WARN] * Port in use: 3000 in sad_lehmann
        Ahora: [WARN] * Port in use: 3000 in flamboyant_morse
        [WARN] * Port in use: 8080 in flamboyant_morse

    [WARN] 5.11 - Ensure that the memory usage for containers is limited (Automated):
        Antes: [WARN] * Container running without memory restrictions: sad_lehmann
        Ahora: [WARN] * Container running without memory restrictions: flamboyant_morse

    [WARN] 5.12 - Ensure that CPU priority is set appropriately on containers (Automated):
        Antes: [WARN] * Container running without CPU restrictions: sad_lehmann
        Ahora: [WARN] * Container running without CPU restrictions: flamboyant_morse

    [WARN] 5.13 - Ensure that the container's root filesystem is mounted as read only (Automated):
        Antes: [WARN] * Container running with root FS mounted R/W: sad_lehmann
        Ahora: [WARN] * Container running with root FS mounted R/W: flamboyant_morse

    [WARN] 5.14 - Ensure that incoming container traffic is bound to a specific host interface (Automated):
        Antes: [WARN] * Port being bound to wildcard IP: 0.0.0.0 in sad_lehmann
        Ahora: [WARN] * Port being bound to wildcard IP: 0.0.0.0 in flamboyant_morse
        [WARN] * Port being bound to wildcard IP: 0.0.0.0 in flamboyant_morse

    [INFO] 5.19 - Ensure that the default ulimit is overwritten at runtime if needed (Manual):
        Antes: [INFO] * Container no default ulimit override: sad_lehmann
        Ahora: [INFO] * Container no default ulimit override: flamboyant_morse

    [WARN] 5.26 - Ensure that the container is restricted from acquiring additional privileges (Automated):
        Antes: [WARN] * Privileges not restricted: sad_lehmann
        Ahora: [WARN] * Privileges not restricted: flamboyant_morse

    [WARN] 5.27 - Ensure that container health is checked at runtime (Automated):
        Antes: [WARN] * Health check not set: sad_lehmann
        Ahora: [WARN] * Health check not set: flamboyant_morse

    [WARN] 5.29 - Ensure that the PIDs cgroup limit is used (Automated):
        Antes: [WARN] * PIDs limit not set: sad_lehmann
        Ahora: [WARN] * PIDs limit not set: flamboyant_morse

    [INFO] 5.30 - Ensure that Docker's default bridge 'docker0' is not used (Manual):
        Antes: [INFO] * Container in docker0 network: sad_lehmann
        Ahora: [INFO] * Container in docker0 network: flamboyant_morse

    [INFO] 6.1 - Ensure that image sprawl is avoided (Manual):
        Antes: [INFO] * There are currently: 4 images
        Ahora: [INFO] * There are currently: 6 images

    [INFO] 6.2 - Ensure that container sprawl is avoided (Manual):
        Antes: [INFO] * There are currently a total of 6 containers, with 1 of them currently running
        Ahora: [INFO] * There are currently a total of 11 containers, with 1 of them currently running

Resumen de las Diferencias

    -Cambios en Nombres de Contenedores: Los contenedores han cambiado de sad_lehmann a flamboyant_morse.
    -Nuevas Advertencias de Puertos: Se han detectado puertos adicionales en uso (8080) y se han reportado más advertencias de puertos abiertos.
    -Más Contenedores y Imágenes: El número de contenedores e imágenes ha aumentado en el sistema.
    -Advertencias y Configuraciones Persistentes: Muchas advertencias persisten con los nuevos contenedores, indicando configuraciones subóptimas similares a las anteriores.

Acciones Recomendadas

    -Configurar Usuarios No Root: Asegúrate de que los contenedores no se ejecuten como root.
    -Añadir Health Checks: Implementa instrucciones HEALTHCHECK en tus Dockerfile.
    -Limitar Recursos: Establece límites de uso de memoria y CPU para los contenedores.
    -Restringir Privilegios: Configura los contenedores para que no adquieran privilegios adicionales.
    -Especificar Interfaces de Red: Asegúrate de que el tráfico de contenedores esté vinculado a interfaces de red específicas.
        
        
