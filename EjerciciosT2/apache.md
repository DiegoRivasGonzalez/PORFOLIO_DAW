# Servidor Web Apache

Diego Rivas González 2ºDAW
---

## Sumario

| Sección | Página |
|---------|--------|
| Servidor Web Apache | 3 |
| Resumen | 3 |
| Actualizar el sistema | 3 |
| Instalar Apache | 3 |
| Verificar la instalación | 3 |
| Configurar usuario y grupo de Apache | 3 |
| Habilitar módulos de Apache | 4 |
| Establecer permisos del directorio de documentos. | 4 |
| Reiniciar Apache | 4 |
| Comprobar estatus. | 4 |
| Comprobación | 6 |
| Prueba con pagina personalizada | 7 |
| Archivo GCI | 9 |
| Archivo .conf | 10 |
| Comprobación | 11 |
| BIBLIOGRAFÍA | 11 |


---


### Resumen

Este documento es una manera de ver como empezar a usar el servidor web de Apache
viendo como se instala desde la consola de comandos, que esta activo y el resultado de
como se ve una pagina una vez esta en funcionamiento.

### Actualizar el sistema

Primero hay que actualizar el sistema. Para ello se utiliza el comando sudo "apt update" y
después sudo "apt upgrade" -y para instalar las actualizaciones disponibles.

### Instalar Apache

Una vez actualizado, se instala el servidor web Apache con el comando sudo "apt install
apache2 -y".

### Verificar la instalación

Para comprobar que Apache está funcionando, se puede obtener la dirección IP del
equipo con "hostname -l". Luego, al escribir esa IP en el navegador, debería aparecer la
página de bienvenida de Apache.

### Configurar usuario y grupo de Apache

Se edita el archivo "/etc/apache2/envvars" con un editor como nano. Dentro de ese
archivo se modifican las líneas para que en lugar de "www-data" se use tu propio usuario
y grupo. Por ejemplo:

![imagen1.jpg](imagen1.jpg)

### Habilitar módulos de Apache

Se activan algunos módulos útiles con los comandos "sudo a2enmod headers y sudo
a2enmod rewrite".

### Establecer permisos del directorio de documentos

Para que el usuario actual tenga permisos sobre la carpeta donde se guardan las páginas, se usa el
comando "sudo chown -R $USER : $USER /var /www/html".

### Reiniciar Apache

Finalmente, se reinicia el servicio para aplicar los cambios con "sudo systemctl restart
apache2".

---

### Comprobar estatus

Una vez reiniciado hacemos el comando para comprobar si esta activo el servicio.

![imagen2.jpg](imagen2.jpg)

---

# Comprobación

En la barra de búsqueda ponemos "localhost/8080" y nos saldrá la siguiente página.

![imagen3.jpg](imagen3.jpg)

---

# Prueba con pagina personalizada

Ahora vamos a cambiar la página que nos aparecía antes modificando el archivo html que tiene.

Para eso ponemos el siguiente comando y abrimos con nano el archivo html.

cd /var/www/html ls nano index.html

Una vez dentro modificamos el contenido del mismo.

![imagen4.jpg](imagen4.jpg)

Ahora si escribimos "localhost" en el navegador nos saldrá nuestra página.

![imagen5.jpg](imagen5.jpg)

---

# Archivo GCI

Ahora vamos a crear una carpeta llamada gci.

sudo mkdir /var/www/gci/

![imagen6.jpg](imagen6.jpg)

Dentro de la carpeta creamos el archivo html de prueba.

![imagen7.jpg](imagen7.jpg)

Ahora ejecutamos los siguientes comandos y cambiamos las líneas del archivo gci.conf.

cd /etc/apache2/sites-available/ sudo cp 000-default.conf gci.conf sudo nano gci.conf

---

# Archivo .conf

Dentro de este archivo ponemos lo siguiente.

![imagen8.jpg](imagen8.jpg)

Y habilitamos este conf con el siguiente comando además de reiniciar el servidor apache para que
aplique los cambios.

sudo a2ensite gci.conf systemctl reload apache2 sudo systemctl daemon-reload sudo systemctl restart apache2 systemctl status apache2


---

# Comprobación

Ponemos en el buscador gci.prueba.com y nos saldrá la página de prueba.

![imagen9.jpg](imagen9.jpg)

---

# BIBLIOGRAFÍA

TUTORIAL GCI: https://ubuntu.com/tutorials/install-and-configure-apache#3-creating-your-own-website  
TUTORIAL INSTALAR APACHE: https://foro.puntocomunica.com/viewtopic.php?t=312
