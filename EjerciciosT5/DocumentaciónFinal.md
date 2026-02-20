# Filezilla: Documentación Técnica Final

## 1. Introducción
En este documento se describe el procedimiento seguido para desplegar un servicio de transferencia de ficheros en nuestro sistema **Ubuntu** y su integración con el servidor web **Apache**.

---

## 2. Instalación del Servidor
Como solución para la gestión de ficheros se ha optado por **vsftpd** debido a su rendimiento y fiabilidad.

* **Comando de instalación:** `sudo apt update && sudo apt install vsftpd`
* **Gestión del servicio:** `sudo systemctl enable vsftpd` `sudo systemctl start vsftpd`

---

## 3. Configuración Básica
El ajuste del servidor se ha llevado a cabo modificando el fichero `/etc/vsftpd.conf`. Los parámetros clave definidos son:

* `anonymous_enable=NO`: Deshabilitar el acceso anónimo.
* `local_enable=YES`: Autorizar el acceso a cuentas locales del sistema.
* `write_enable=YES`: Activar los permisos de escritura y edición.
* `chroot_local_user=YES`: Confinamiento del usuario a su propio directorio como medida de seguridad.

---

## 4. Usuarios y Permisos
Se ha establecido un entorno en el que el usuario FTP comparte identidad con el responsable del contenido web.

* **Usuario:** `ftpuser`
* **DocumentRoot:** `/var/www/html`
* **Asignación de permisos:**
    * Propietario: `ftpuser`
    * Grupo: `www-data`
    * Permisos: `755` para directorios y `644` para ficheros.

---

## 5. Seguridad (FTPS)
Con el objetivo de proteger la transmisión de datos frente a posibles interceptaciones, se ha configurado **FTP sobre TLS**:

1.  **Generación del certificado:** Empleo de OpenSSL para producir una clave privada y un certificado autofirmado.
2.  **Parámetros SSL:**
    * `ssl_enable=YES`
    * `force_local_data_ssl=YES` (Cifrado en la transferencia de ficheros).
    * `force_local_logins_ssl=YES` (Cifrado en el inicio de sesión).

---

## 6. Modos de Conexión

### Modo Activo vs. Pasivo
Se ha dado preferencia al **Modo Pasivo** para evitar incompatibilidades con cortafuegos del lado del cliente y con NAT.

* **Configuración en modo pasivo:**
    * `pasv_min_port=50000`
    * `pasv_max_port=51000`
* **Razonamiento:** En el modo pasivo es el propio cliente quien establece la conexión de datos, lo que facilita la comunicación a través de redes con NAT o routers domésticos.

---

## 7. Herramientas Cliente Empleadas

1.  **FileZilla:** Cliente principal utilizado para realizar transferencias seguras mediante cifrado TLS.
2.  **Gestor de Archivos (Nautilus):** Empleado para pruebas de compatibilidad básica y acceso rápido al servidor.
3.  **Navegador Web:** Utilizado para comprobar la correcta publicación del contenido mediante HTTP.
