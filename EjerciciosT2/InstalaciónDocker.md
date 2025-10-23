## INSTALACIÓN DOCKER-DESKTOP  
**Diego Rivas González**  
**2º DAW**

---
Lo primero será actualizar el sistema para tener todo listo y evitar fallos.

![imagen2](/imagenes2/imagen2.png)

Instalamos los paquetes requeridos para docker.

![imagen3](/imagenes2/imagen3.png)

Instalamos el **docker engine**, la interfaz de línea de comandos, el runtime y los plugins para **docker compose**.

![imagen4](/imagenes2/imagen4.png)

---
## COMPROBAR ESTADO DOCKER  

Comprobamos el estado de docker y vemos que está activo y funcionando.

![imagen5](/imagenes2/imagen5.png)

---
## UTILIZAR DOCKER SIN SUDO  
Al hacer este comando vemos que no funciona sin utilizar `sudo` para que funcione vamos a hacer lo siguiente.

![imagen6](/imagenes2/imagen6.png)

Damos permisos al usuario y reiniciamos.

![imagen7](/imagenes2/imagen7.png)

Y hacemos el comando sin `sudo` para ver que funciona correctamente.

![imagen8](/imagenes2/imagen8.png)

---
## INSTALACIÓN DE CONTENEDORES DE SERVIDOR WEB Y APLICACIONES  
Buscaremos la imagen del servidor web que sera **Nginx** con este comando.
![imagen9](/imagenes2/imagen9.png)

Y el de aplicaciones que será **Tomcat**.
Después iniciaremos los contenedores con estos comandos.

![imagen10](/imagenes2/imagen10.png)

---
## INICIAR CONTENEDORES  
Después iniciaremos los contenedores con estos comandos
![imagen11](/imagenes2/imagen11.png)
![imagen12](/imagenes2/imagen12.png)

---
## VERIFICAR ESTADO  
Verificamos que están activos.
![imagen13](/imagenes2/imagen13.png)

---
## COMPROBAR EN NAVEGADOR  

Y comprobamos en un navegador.
![imagen14](/imagenes2/imagen14.png)
![imagen15](/imagenes2/imagen15.png)

# DESCRIPCIÓN DE LOS REQUERIMIENTOS MÍNIMOS PARA IMPLANTAR UNA APLICACIÓN WEB

A continuación se detallan los **requerimientos mínimos** necesarios para implantar una aplicación web, considerando el hardware, software, red, configuración del servidor y aspectos de seguridad y mantenimiento.

---

## REQUISITOS DE HARDWARE Y SOFTWARE

Para la correcta instalación y funcionamiento de una aplicación web es necesario disponer de los siguientes recursos:

### Hardware
- **Procesador:** CPU de al menos 2 núcleos (recomendado 4 núcleos o más).  
- **Memoria RAM:** Mínimo 4 GB (recomendado 8 GB o más).  
- **Almacenamiento:** Al menos 20 GB de espacio libre en disco.  
- **Conectividad:** Tarjeta de red con soporte Ethernet o Wi-Fi estable.  
- **Virtualización:** Soporte activo en BIOS/UEFI (para entornos con máquinas virtuales o contenedores Docker).  

### Software
- **Sistema operativo:** Ubuntu 24.04 LTS (o cualquier distribución Linux estable).  
- **Servidor web:** Nginx o Apache.  
- **Servidor de aplicaciones:** Tomcat o Node.js según el tipo de aplicación.  
- **Base de datos:** MySQL, PostgreSQL o MongoDB.  
- **Docker / Docker Compose:** Para el despliegue y gestión de contenedores.  
- **Herramientas adicionales:** Git, curl, y un editor de texto (VS Code, Nano, etc.).  

---

## INFRAESTRUCTURA DE RED

La infraestructura de red debe estar diseñada para garantizar el acceso rápido, seguro y confiable a la aplicación.

- **Dirección IP fija o DNS dinámico** para acceso externo.  
- **Router o firewall configurado** con los puertos necesarios abiertos (por ejemplo, 80 y 443).  
- **Segmentación de red** para aislar los entornos de desarrollo, pruebas y producción.  
- **Ancho de banda suficiente** para el tráfico esperado de usuarios.  
- **Monitoreo de red** para detectar incidencias y optimizar el rendimiento.  

---

## CONFIGURACIÓN DEL SERVIDOR WEB Y DE APLICACIONES

Para implantar correctamente el entorno, es necesario realizar la configuración adecuada de los servidores involucrados:

### Servidor Web (Nginx)
- Configurar los bloques de servidor (`server blocks`) para la aplicación.  
- Habilitar los módulos necesarios (proxy, gzip, etc.).  
- Configurar certificados SSL/TLS para acceso seguro (HTTPS).  

### Servidor de Aplicaciones (Tomcat)
- Definir correctamente el **contexto de la aplicación** (`/app` o raíz).  
- Asignar memoria JVM apropiada según el tamaño de la aplicación.  
- Configurar los puertos de escucha (por defecto 8080) y las conexiones al servidor web mediante proxy inverso.  

---

## SEGURIDAD Y MANTENIMIENTO

El entorno debe contar con medidas básicas de protección, actualización y respaldo.

- **Cortafuegos (firewall)** configurado con reglas restrictivas.  
- **Actualizaciones automáticas** del sistema operativo y dependencias.  
- **Certificados SSL válidos** y renovación automática (por ejemplo, con Let’s Encrypt).  
- **Copia de seguridad periódica** de bases de datos y archivos.  
- **Monitoreo del sistema** (uso de CPU, memoria, logs, etc.).  
- **Control de acceso por roles** y autenticación de usuarios segura.  

