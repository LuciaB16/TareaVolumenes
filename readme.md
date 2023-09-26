# Tarea: Trabajando con volumenes

### Sigue los apuntes de Docker para realizar la siguiente práctica:

Utilizaremos la imagen de Apache, tag 2.4. Usa Visual Studio Code y Docker junto con esta imagen para seguir las siguientes instrucciones.

---

1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.
2. Crea un contenedor con el nombre 'dam_web1'.
3. Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?.
4. Utiliza bind mount para que el directorio del apache2 'htdocs' este montado un directorio que tu elijas.
Utiliza -v "$PWD"/htdocs:/usr/local/apache2/htdocs/
5. Realiza un 'hola mundo' en html (usa Code) y comprueba que accedes desde el navegador.
6. Crea otro contenedor 'dam_web2' con el mismo volumen y a otro puerto, por ejemplo 9080.
7. Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador:
http://localhost:9080 
http://localhost:8000
8. Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página