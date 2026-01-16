# Configuración de Reverse Proxy hacia Tomcat

## Entorno
- Apache HTTP Server
- Apache Tomcat
- Ubuntu Server

## Pasos

1. Instalación de Apache y módulos:
   - `sudo apt install apache2`
   - `sudo a2enmod proxy proxy_http` (o `proxy_ajp`)

2. Configuración de VirtualHost:
   - Archivo: `/etc/apache2/sites-available/tomcat_proxy.conf`
   - ProxyPass hacia `http://localhost:8080/` o `ajp://localhost:8009/`

3. Activación del sitio:
   - `sudo a2ensite tomcat_proxy.conf`
   - `sudo systemctl reload apache2`

4. Configuración de Tomcat:
   - Verificar conector AJP en `server.xml`
   - Reiniciar Tomcat

5. Verificación:
   - Acceso vía navegador
   - Logs en `/var/log/apache2/`

## Resultado
La aplicación web responde correctamente a través del servidor Apache, redirigiendo hacia Tomcat.
