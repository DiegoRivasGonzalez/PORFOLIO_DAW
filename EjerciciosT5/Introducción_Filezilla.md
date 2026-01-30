# 📁 FileZilla Server: conceptos básicos y arquitectura

## 1. Introducción a los servidores FTP / FTPS
Un servidor **FTP (File Transfer Protocol)** es un servicio que permite intercambiar archivos entre un cliente y un servidor a través de una red basada en TCP/IP. Sigue un modelo cliente–servidor, donde el cliente inicia la conexión y solicita acciones como listar carpetas, subir o descargar ficheros.

El protocolo FTP original no cifra la información, por lo que usuarios y contraseñas viajan en texto plano. Para solucionar esto aparece **FTPS**, que añade cifrado mediante SSL/TLS. Por otro lado, **SFTP** es un protocolo diferente que funciona sobre SSH y no pertenece a la familia FTP.

---

## 2. Diferencias entre FTP, FTPS y SFTP
- **FTP**: utiliza conexiones TCP sin cifrar, normalmente por el puerto 21, lo que lo hace inseguro en redes públicas.  
- **FTPS**: mantiene el funcionamiento de FTP, pero protege las comunicaciones con SSL/TLS.  
- **SFTP**: se basa en SSH, usa un único canal cifrado (puerto 22) y no comparte arquitectura con FTP ni FTPS.

---

## 3. Arquitectura cliente–servidor
El protocolo FTP se apoya en dos componentes: el **cliente FTP**, que inicia la sesión, y el **servidor FTP**, que responde a las peticiones. A diferencia de otros protocolos, FTP emplea dos conexiones separadas:

- Un **canal de control**, que permanece activo durante toda la sesión.  
- Un **canal de datos**, que se abre y se cierra en cada transferencia.

Esta separación permite gestionar comandos y envío de información de forma independiente.

---

## 4. Canal de control
El canal de control se encarga de la **autenticación del usuario y del envío de comandos FTP**. Se crea al iniciar la sesión y se mantiene abierto hasta que el cliente se desconecta. De forma predeterminada, utiliza el **puerto TCP 21**.

Por este canal viajan órdenes como iniciar sesión, listar directorios o solicitar transferencias, pero nunca los datos de los archivos.

---

## 5. Canal de datos
El canal de datos se usa exclusivamente para la **transferencia de archivos y listados de directorios**. No es permanente, sino que se crea y se cierra cada vez que se realiza una operación.

Su comportamiento varía según el modo de funcionamiento: activo o pasivo.

---

## 6. Modo activo
En el modo activo, el cliente abre primero el canal de control con el servidor por el puerto 21. Después, indica al servidor en qué puerto local espera recibir datos. Cuando comienza la transferencia, el servidor establece la conexión de datos desde su **puerto 20** hacia el puerto del cliente.

Este modo suele presentar problemas con firewalls y NAT, ya que el cliente debe aceptar conexiones entrantes.

---

## 7. Modo pasivo
En el modo pasivo, el cliente también inicia el canal de control. Sin embargo, cuando se necesita transferir información, el servidor informa al cliente de un puerto disponible dentro de un rango configurado. El cliente es quien abre la conexión hacia ese puerto.

Este es el modo más utilizado hoy en día, ya que evita conflictos con firewalls y permite que todas las conexiones sean iniciadas por el cliente.

---

## 8. Puertos utilizados
- **Puerto 21**: canal de control.  
- **Puerto 20**: canal de datos en modo activo.  
- **Rango configurable**: canal de datos en modo pasivo.

Una correcta apertura y configuración de estos puertos es esencial para el funcionamiento del servicio.

---

## 9. Conclusión
FTP se basa en una arquitectura cliente–servidor con **dos canales independientes**. Comprender la diferencia entre canal de control y canal de datos, así como entre modo activo y pasivo, es fundamental para entender su funcionamiento.
