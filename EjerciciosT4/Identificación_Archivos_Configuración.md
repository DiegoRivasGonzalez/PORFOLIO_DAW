# Archivos de Configuración de Tomcat

Los archivos clave de Tomcat se encuentran todos en $CATALINA_BASE/conf/

---

## 1. `server.xml`
Archivo principal de configuración del servidor Tomcat. Controla cómo arranca, qué puertos usa y cómo se comportan los hosts virtuales.

### Funciones principales
- Definir el servidor y su puerto de apagado.
- Configurar servicios y conectores.
- Gestionar hosts virtuales.
- Definir el motor (`Engine`) y los `Realms`.

### Elementos configurables
- `<Server>`: puerto de apagado.
- `<Service>`: agrupa conectores y contenedores.
- `<Connector>`: puertos HTTP/HTTPS, protocolo, TLS, buffers, compresión.
- `<Engine>`: procesamiento de peticiones.
- `<Host>`: despliegue de aplicaciones, logs, valves.
- `<Realm>`: autenticación (incluye referencia a `tomcat-users.xml`).

---

## 2. `web.xml` (global)
Descriptor de despliegue por defecto para todas las aplicaciones web.  
Cada aplicación puede sobrescribirlo con su propio `WEB-INF/web.xml`.

### Funciones principales
- Definir servlets y filtros globales.
- Configurar MIME types.
- Establecer páginas de error globales.
- Configurar el timeout de sesión.
- Definir listeners globales.

### Elementos configurables
- `<servlet>` y `<servlet-mapping>`
- `<filter>` y `<filter-mapping>`
- `<mime-mapping>`
- `<error-page>`
- `<session-config>`
- `<listener>`

---

## 3. `tomcat-users.xml`
Archivo que define usuarios y roles cuando Tomcat usa `MemoryRealm` o `UserDatabaseRealm`.

### Funciones principales
- Crear usuarios.
- Asignar roles.
- Controlar acceso al Manager y Host Manager.

### Elementos configurables
- `<role rolename="..."/>`
- `<user username="..." password="..." roles="..."/>`

---

## 4. `context.xml` (global)
Define el comportamiento por defecto de los contextos de aplicaciones web.  
Puede existir a nivel global o dentro de cada aplicación.

### Funciones principales
- Configurar recursos JNDI.
- Definir parámetros de entorno.
- Configurar el Session Manager.
- Añadir valves específicos.
- Controlar recarga, rutas y recursos vigilados.

### Elementos configurables
- `<Context>`
- `<Resource>` (datasources, mail, etc.)
- `<Environment>`
- `<Manager>`
- `<Valve>`
- `<Loader>`
- `<WatchedResource>`

---

# Mapa visual de dependencias

     server.xml        
    - Conectores        
     - Hosts              
     - Realms            

▼

    context.xml        
    (global o por app)     
    - JNDI Resources     
    - Session Manager       
    - Valves              

▼

       web.xml           
       (global o por app)     
       - Servlets/Filtros    
       - Error pages         
       - MIME types          

▼      
        tomcat-users.xml      
        - Roles               
        - Usuarios            

| Archivo              | Función principal                                   |
|----------------------|-----------------------------------------------------|
| `server.xml`         | Configuración del servidor, puertos, hosts, realms  |
| `web.xml`            | Configuración global de servlets y filtros          |
| `tomcat-users.xml`   | Usuarios y roles para autenticación interna         |
| `context.xml`        | Configuración de aplicaciones y recursos JNDI       |

