# Tomcat: Investigación y descripción

## Catalina
Tomcat es un servidor de aplicaciones Java, y **Catalina** es su contenedor principal de servlets y JSP (JavaServer Pages).  
Es el corazón de Tomcat y se encarga de implementar las especificaciones Java necesarias para ejecutar aplicaciones web dinámicas.

Catalina gestiona el ciclo de vida de los servlets y procesa las peticiones HTTP mediante componentes como:

- **Coyote** → conector HTTP  
- **Jasper** → motor JSP  

---

## Coyote
**Coyote** es un conector compatible con HTTP/1.1 y HTTP/2.  
Permite que Catalina funcione también como servidor web simple, sirviendo archivos locales como documentos HTTP.

---

## Jasper
**Jasper** es el motor de JSP de Apache Tomcat.

Su funcionamiento:

- Analiza archivos `.jsp`
- Los compila a **servlets Java**
- Catalina los ejecuta
- Detecta cambios en JSP y recompila automáticamente

---

## Manager y Host Manager
Tomcat incluye dos interfaces administrativas:

### Manager
Permite:

- Desplegar aplicaciones (WAR)
- Parar/recargar servicios
- Administrar aplicaciones sin reiniciar el servidor

### Host Manager
Permite crear y gestionar **hosts virtuales**.

Ambas interfaces requieren autenticación configurada en `tomcat-users.xml` mediante usuarios y roles.

---

## Estructura de directorios

- **bin/** – Scripts de arranque y apagado  
- **conf/** – Archivos de configuración (server.xml, tomcat-users.xml, etc.)  
- **webapps/** – Aplicaciones desplegadas (WAR o carpetas)  
- **lib/** – Librerías compartidas  
- **logs/** – Registros de actividad y errores  

---

## Flujo interno de funcionamiento

1. **Coyote** recibe la petición del cliente  
2. La entrega a **Catalina**  
3. Catalina selecciona el contenedor del servlet/JSP  
4. **Jasper** compila el JSP si es necesario  
5. El servlet genera la respuesta  
6. **Coyote** envía la respuesta al cliente  

