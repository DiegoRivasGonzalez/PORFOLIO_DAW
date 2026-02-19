# 📝Filezilla: Gestión de cuentas y agrupaciones

## 1. Generar un grupo con privilegios reducidos
El primer paso consiste en crear un grupo destinado a los usuarios que utilizarán el servicio FTP:  
`sudo groupadd ftp_limitado`.  

Este grupo permitirá administrar permisos de forma conjunta para todos sus miembros.

## 2. Preparar el directorio principal del FTP
Seguidamente creamos la carpeta que actuará como directorio inicial para el grupo:  
`sudo mkdir -p /srv/ftp/limitado`.  

Luego asignamos la propiedad del grupo:  
`sudo chown root:ftp_limitado /srv/ftp/limitado`  
y aplicamos permisos restringidos:  
`sudo chmod 750 /srv/ftp/limitado`.  

Interpretación de los permisos:
- **root:** lectura, escritura y ejecución  
- **ftp_limitado:** lectura y ejecución  
- **otros usuarios:** sin acceso

## 3. Añadir usuarios vinculados al grupo
Ahora incorporamos dos cuentas que utilizaremos en la práctica:

- **Usuario 1**  
  `sudo useradd -m -G ftp_limitado -d /srv/ftp/limitado usuario1`  
  `sudo passwd usuario1`  
  Contraseña: qwerty$2001  

- **Usuario 2**  
  `sudo useradd -m -G ftp_limitado -d /srv/ftp/limitado usuario2`  
  `sudo passwd usuario2`  
  Contraseña: qwerty$2002  

Ambos usuarios quedan asociados al grupo `ftp_limitado` y comparten el mismo directorio raíz.

## 4. Ajustar permisos de escritura y eliminación
En este punto editamos el archivo de configuración de **vsftpd** para habilitar operaciones como subir, borrar o modificar archivos.  

Debe aparecer algo similar a lo siguiente:

![img](https://github.com/AdriCarrasco22/Porfolio_Adrian_Carrasco_DAW/blob/main/UT5%3AFilezilla/Ejercicios/Imagenes/img1_actividadUsuarios.png)

Estas opciones permiten:
- Cargar archivos al servidor  
- Eliminar elementos  
- Editar contenido existente

## 5. Establecer el directorio raíz (chroot)
Para impedir que los usuarios naveguen fuera de su carpeta asignada, verificamos que la configuración incluya:

![img](https://github.com/AdriCarrasco22/Porfolio_Adrian_Carrasco_DAW/blob/main/UT5%3AFilezilla/Ejercicios/Imagenes/img2_actividadUsuarios.png)

Con esto, cada usuario queda confinado a su directorio FTP.

## 6. Limitar conexiones simultáneas
A continuación configuramos un límite de acceso: máximo 10 conexiones totales y un máximo de 2 por dirección IP.

`max_clients=10`  
`max_per_ip=2`

## 7. Verificaciones finales
Primero comprobamos que el grupo y los usuarios existen:  
`getent group ftp_limitado`.  

Después realizamos una conexión de prueba:  
`ftp 10.0.2.15`.  

![img](https://github.com/AdriCarrasco22/Porfolio_Adrian_Carrasco_DAW/blob/main/UT5%3AFilezilla/Ejercicios/Imagenes/img3_actividadUsuarios.png)

Se confirma así que el grupo y los usuarios están correctamente creados y que el acceso FTP funciona.

## 8. Diferencias entre permisos de usuario y de grupo
Los **permisos individuales** determinan qué puede hacer un usuario concreto sobre un archivo o carpeta (leer, modificar, eliminar). Permiten un control detallado sobre cada cuenta.

Los **permisos de grupo** se aplican a todos los miembros de un mismo conjunto, facilitando la administración cuando varios usuarios requieren los mismos privilegios. En entornos FTP, esto simplifica la gestión y evita configuraciones repetitivas.
