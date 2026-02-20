# Flujo de Publicación Web: FTP a DocumentRoot

## 1. Configuración del Directorio FTP y Web (DocumentRoot)

Para que los archivos subidos por FTP sean visibles en la web, el **Home Directory** del usuario FTP debe coincidir con el **DocumentRoot** del servidor web.

* **Ruta estándar en Linux:** `/var/www/html`
* **Configuración en Apache:** Se define en el archivo de VirtualHost (`/etc/apache2/sites-available/000-default.conf`) mediante la directiva `DocumentRoot`.
* **Configuración en FTP (vsftpd/ProFTPD):** Se debe asignar al usuario FTP el mismo directorio de trabajo:
   



---

## 2. Gestión de Permisos y Propiedad

Es crucial que tanto el servidor FTP como el servicio Web puedan leer/escribir en la carpeta.
1.  **Propiedad:** El usuario FTP debe tener permisos de escritura.
2.  **Grupo:** El servidor web (ej. `www-data`) debe tener permisos de lectura.
    ```bash
    chown -R usuario1:www-data /var/www/html
    chmod -R 755 /var/www/html
    ```

---

## 3. Subida del archivo HTML vía FTP

Utilizando un cliente dedicado como **FileZilla**, el flujo es el siguiente:

1.  **Conexión:** Introducir IP, usuario, contraseña y puerto (21 o 2121).
2.  **Localización:** En el panel izquierdo (Local), seleccionar el archivo `index.html`.
3.  **Transferencia:** Arrastrar el archivo al panel derecho (Remoto), que apunta a `/var/www/html`.
4.  **Confirmación:** El cliente debe devolver un mensaje de `Transferencia completada con éxito`.

---

## 4. Acceso vía HTTP desde el Navegador

Una vez el archivo reside en el servidor, el servidor web (Apache o Nginx) lo sirve automáticamente a través del protocolo HTTP/HTTPS.

* **Acceso:** Abrir el navegador e ingresar la IP o dominio:
    `http://127.0.0.1/index.html` 
* **Resultado:** El navegador interpreta el código HTML y renderiza la página web.

---

## 5. Descripción del Flujo Completo de Publicación

El ciclo de vida de una actualización web mediante este método sigue este esquema:

1.  **Desarrollo Local:** El programador crea o edita el archivo `.html` en su ordenador.
2.  **Transporte (FTP):** El cliente FTP establece un túnel para enviar los datos al servidor.
3.  **Almacenamiento:** Los archivos se depositan en el sistema de archivos del servidor, específicamente en la ruta que el servidor web monitoriza.
4.  **Despliegue (HTTP):** El servidor web detecta el nuevo archivo y lo entrega a cualquier usuario que realice una petición mediante una URL.
