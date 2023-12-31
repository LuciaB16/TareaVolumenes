# Tarea: Trabajando con volúmenes

### Sigue los apuntes de Docker para realizar la siguiente práctica:

Utilizaremos la imagen de Apache, tag 2.4. Usa Visual Studio Code y Docker junto con esta imagen para seguir las siguientes instrucciones.

---

**1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.**

`$ docker pull httpd` -> Para descargar la imagen.

`$ docker image ls` -> Para comprobar que la imagen esá en el equipo.

**2. Crea un contenedor con el nombre 'dam_web1'.**

`$ docker run -d --name dam_web1 httpd` -> Crea el contenedor con dicho nombre que le especifico.

**3. Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?.**

Antes de lanzar este comando, debo borrar el contenedor si está iniciado.

`$ docker run -dit --name dam_web1 -p 8080:80 httpd:2.4` -> Con este comando mapeo el puerto del host con el puerto del contenedor.

`$ ip address` -> Muestra la dirección IP de mi equipo, que es *10.0.9.15*

Pongo en el navegador 10.0.9.15:8080 y veo que funciona.

**4. Utiliza bind mount para que el directorio del apache2 'htdocs' este montado un directorio que tu elijas.
Utiliza -v "$PWD"/htdocs:/usr/local/apache2/htdocs/**

Ya tenemos montado el directorio htdocs en apache2 de tareas anteriores.

Para mapear los puertos del contenedor y el directorio, lanzamos el siguiente comando:

`$ docker run -dit --name dam_web1 -p 8080:80 -v /home/dam2/Documentos/SXE/APACHE/htdocs:/usr/local/apache2/htdocs/ httpd:2.4`

Previamente a esto, hay que borrar el contenedor para que funcione la ejecución de dicho comando.

**5. Realiza un 'hola mundo' en html (usa Code) y comprueba que accedes desde el navegador.**

Modificamos el html del archivo index.html y escribimos 'hola mundo'. Posteriormente lo comprobamos en el navegador, escribiendo lo siguiente:

`10.0.9.15:8080` y nos aparece 'hola mundo'

**6. Crea otro contenedor 'dam_web2' con el mismo volumen y a otro puerto, por ejemplo 9080.**

`$ docker run -dit --name dam_web2 -p 9080:80 -v /home/dam2/Documentos/SXE/APACHE/htdocs:/usr/local/apache2/htdocs/ httpd:2.4` -> Es el mismo comando que en el apartado 4 pero cambiando el nombre del contenedor y el puerto del host.

**7. Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador:**
http://localhost:9080 

http://localhost:8080

Comprobamos que en ambos aparece 'Hola mundo', escribiendo dichas direcciones web en el navegador.

**8. Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página.**

Efectivamente, haciendo modificaciones en el html nombrado previamente, vemos que aparecen en los dos servidores esos cambios.