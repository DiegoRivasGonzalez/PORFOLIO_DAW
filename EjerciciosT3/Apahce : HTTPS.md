# Servidor Web Apache

## Resumen
Este documento muestra cómo empezar a usar el servidor web Apache, cómo instalarlo desde la consola de comandos, comprobar que está activo y visualizar el resultado en el navegador.

## Actualizar el sistema
Primero actualizamos el sistema:

```
sudo apt update
sudo apt upgrade -y
```

## Instalar Apache
Instalamos Apache:

```
sudo apt install apache2 -y
```

## Verificar la instalación
Para comprobar que Apache está funcionando obtenemos la IP del equipo:

```
hostname -I
```

Después introducimos esa IP en el navegador y veremos la página de bienvenida de Apache.

![imagen1.jpg](/imagenesHTTPS/imagen1.png)

## Configurar usuario y grupo de Apache
Editamos el archivo:

```
sudo nano /etc/apache2/envvars
```

Modificamos las líneas donde aparezca `www-data` para usar nuestro propio usuario y grupo.

![imagen3.jpg](/imagenesHTTPS/imagen2.png)

## Habilitar módulos de Apache
Activamos módulos útiles:

```
sudo a2enmod headers
sudo a2enmod rewrite
```

## Establecer permisos del directorio de documentos
Para dar permisos al usuario actual sobre `/var/www/html`:

```
sudo chown -R $USER:$USER /var/www/html
```

## Reiniciar Apache
Reiniciamos el servicio:

```
sudo systemctl restart apache2
```

## Comprobar estatus
Comprobamos que el servicio está activo:

![imagen3.jpg](/imagenesHTTPS/imagen3.png)

## Comprobación
En el navegador escribimos:

```
localhost:8080
```

Y veremos la página por defecto de Apache.

![imagen4.jpg](/imagenesHTTPS/imagen4.png)

## Prueba con página personalizada
Ahora modificamos la página HTML principal:

```
sudo nano /var/www/html/index.html
```

Editamos el contenido del archivo.

![imagen5.jpg](/imagenesHTTPS/imagen5.png)

Después recargamos el navegador escribiendo:

```
localhost
```

Y aparecerá nuestra página personalizada.

![imagen6.jpg](/imagenesHTTPS/imagen6.png)

## Archivo GCI
Creamos una carpeta llamada `gci`:

```
mkdir /var/www/html/gci
```

Dentro creamos un archivo HTML de prueba.

```
sudo nano /var/www/html/gci/index.html
```

Luego editamos el archivo de configuración `gci.conf`.

![imagen7.jpg](/imagenesHTTPS/imagen7.png)

## Archivo .conf
Dentro del archivo `gci.conf` colocamos la configuración necesaria.

Habilitamos el sitio:

```
sudo a2ensite gci.conf
sudo systemctl restart apache2
```

## Comprobación
En el navegador escribimos:

```
gci.prueba.com
```

Y aparecerá la página de prueba.

## Bibliografía
TUTORIAL GCI: https://ubuntu.com/tutorials/install-and-configure-apache#3-creating-your-own-website  
TUTORIAL INSTALAR APACHE: https://foro.puntocomunica.com/viewtopic.php?t=312

