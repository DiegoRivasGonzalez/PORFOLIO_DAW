# FileZilla: Verificación en Modo Activo y Modo Pasivo

## 1. Definición del rango de puertos para modo pasivo

Para que el modo pasivo funcione correctamente, el servidor debe disponer de un conjunto de puertos destinados a la transferencia de datos.  

Editamos el archivo de configuración con:

`sudo nano /etc/vsftpd.conf`

Añadimos o comprobamos las siguientes líneas:

`pasv_enable=YES`  
`pasv_min_port=50000`  
`pasv_max_port=51000`  

Significado de cada directiva:

- `pasv_enable=YES` → Activa el funcionamiento en modo pasivo.
- `pasv_min_port` y `pasv_max_port` → Establecen el intervalo de puertos que el servidor utilizará para las conexiones de datos.

De esta forma, el servidor queda preparado para aceptar conexiones pasivas dentro del rango indicado.

---

## 2. Comprobación del funcionamiento

### 🔹 Conexión en modo activo

Ejecutamos:

`ftp 10.0.2.15`

Por defecto, el cliente FTP intentará trabajar en modo activo.  
En este modo:

- El cliente inicia la conexión de control al puerto 21 del servidor.
- El servidor abre la conexión de datos hacia el cliente.

Si el equipo cliente no tiene restricciones de firewall, podremos listar y descargar archivos sin problema.

---

### 🔹 Conexión en modo pasivo

Dentro del cliente FTP activamos el modo pasivo:

`passive`

Posteriormente volvemos a conectarnos:

`ftp 10.0.2.15`

En este caso:

- El cliente abre tanto la conexión de control como la de datos.
- El servidor responde utilizando un puerto comprendido entre 50000 y 51000.
- Es un método más compatible con redes que utilizan NAT o firewall.

Al descargar el mismo archivo de prueba, observaremos que la comunicación se realiza correctamente mediante el puerto pasivo asignado.

---

## 3. Comparación entre ambos modos

| Modo       | Funcionamiento del canal de datos                                | Puntos fuertes                                              | Limitaciones                                                  |
|------------|------------------------------------------------------------------|-------------------------------------------------------------|---------------------------------------------------------------|
| **Activo** | El servidor inicia la conexión hacia el cliente                  | Configuración sencilla en redes sin restricciones           | Puede fallar si el cliente está protegido por firewall o NAT |
| **Pasivo** | El cliente inicia la conexión hacia el servidor                  | Compatible con firewall y NAT; más práctico en Internet     | Necesita definir previamente un rango de puertos en el servidor |

---

