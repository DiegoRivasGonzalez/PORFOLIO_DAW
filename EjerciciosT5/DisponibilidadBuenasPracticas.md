# Filezilla: Disponibilidad y Buenas Prácticas

## 1. Guía de Recomendaciones: Servidor FTP en Entorno Real

  * Control de Conexiones (Asegurar la Disponibilidad):

    Con el fin de prevenir que un único usuario o un ataque de Denegación de Servicio (DoS) colapse el servidor, es necesario establecer restricciones sobre los recursos disponibles:
       **Máximo de conexiones por IP:** Definir un límite de sesiones simultáneas desde una misma dirección IP (por ejemplo, entre 3 y 5 conexiones).
       **Control del ancho de banda:** Fijar una velocidad máxima de transferencia mediante el parámetro `local_max_rate` en vsftpd, evitando que el tráfico FTP comprometa el rendimiento del servidor web.
       **Cierre por inactividad (Timeout):** Configurar el cierre automático de sesiones que permanezcan inactivas, liberando así puertos y memoria del sistema.

---

  * Registros y Auditoría (Trazabilidad):

    En un entorno de producción, resulta imprescindible conocer quién accedió, en qué momento y qué modificaciones realizó:
       **Registro detallado activo:** Verificar que los parámetros `xferlog_enable=YES` y `log_ftp_protocol=YES` se encuentren habilitados en el fichero de configuración.
       **Gestión centralizada de logs:** Redirigir los registros hacia `/var/log/vsftpd.log` y apoyarse en herramientas como `Logrotate` para gestionar el tamaño de los ficheros de log y evitar que saturen el disco.
       **Revisión de errores de acceso:** Examinar de forma periódica los intentos de autenticación fallidos, ya que pueden ser indicativos de ataques por fuerza bruta.

---

  * Copias de Seguridad (Integridad de los Datos):

    El servicio FTP actúa como punto de entrada al sistema; ante cualquier pérdida o borrado accidental, debe existir un plan de contingencia:
       **Copia del fichero de configuración:** Guardar siempre una copia de respaldo de `/etc/vsftpd.conf` antes de aplicar cualquier modificación.
       **Backups automáticos programados:** Utilizar tareas Cron para ejecutar copias de seguridad diarias de los directorios FTP (`/var/www/html`) hacia un almacenamiento externo o remoto.
       **Estrategia 3-2-1:** Conservar 3 copias de los datos, distribuidas en 2 soportes de distinta naturaleza, y al menos 1 de ellas ubicada fuera del servidor principal para maximizar la resiliencia.

---

  * Cortafuegos y NAT (Seguridad de Red):

    El servidor no debería quedar totalmente expuesto a Internet sin ningún tipo de filtrado:
       **Rango de puertos pasivos:** Definir un intervalo concreto de puertos para el modo pasivo (p. ej. 50000-51000) y habilitarlos únicamente en las reglas del cortafuegos.
       **Protección ante fuerza bruta:** Instalar y configurar `Fail2Ban`, herramienta que bloquea de forma automática las direcciones IP que acumulan varios intentos de acceso con credenciales incorrectas.
       **Restricción del puerto FTP:** Cerrar el puerto 21 para el tráfico general, permitiendo únicamente el acceso desde IPs de confianza, o bien cambiar el puerto por defecto para reducir la exposición frente a escaneos automatizados.
