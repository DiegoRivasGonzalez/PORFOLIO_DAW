# 📦 1. DESCARGAR O GENERAR UN WAR DE EJEMPLO

## Opción A: Descargar un WAR ya hecho
Puedes descargar un WAR de ejemplo desde cualquier repositorio público.  
Ejemplo (Hello World básico):

wget https://tomcat.apache.org/tomcat-10.1-doc/appdev/sample/sample.war

## Opción B: Generar tu propio WAR con un Hello World JSP

Estructura mínima del proyecto:

helloworld/
 ├── index.jsp
 └── WEB-INF/
      └── web.xml

Contenido de WEB-INF/web.xml:

<web-app>
    <display-name>HelloWorld</display-name>
</web-app>

Generar el WAR:

cd helloworld
jar -cvf helloworld.war index.jsp WEB-INF


# 🚀 2. DESPLEGAR EL WAR EN TOMCAT

Copia el WAR a la carpeta webapps del Tomcat que está en ejecución:

sudo cp helloworld.war /var/lib/tomcat10/webapps/

Reinicia Tomcat (si quieres forzar redeploy):

sudo systemctl restart tomcat10


# 🔍 3. OBSERVAR EL DESPLIEGUE AUTOMÁTICO

Cuando Tomcat detecta un archivo .war en webapps/, realiza automáticamente estos pasos internos:

1. **Detecta el WAR nuevo**
   - Tomcat escanea periódicamente la carpeta webapps/.
   - Si encuentra un .war nuevo o modificado, inicia el proceso de despliegue.

2. **Crea una carpeta con el mismo nombre que el WAR**
   - Ejemplo:
     helloworld.war → helloworld/

3. **Descomprime el WAR dentro de esa carpeta**
   - Copia todos los JSP, clases, librerías y configuración.

4. **Compila los JSP**
   - Cada .jsp se convierte en un servlet Java.
   - El servlet generado se guarda en:
     /var/lib/tomcat10/work/Catalina/localhost/helloworld/

5. **Carga el web.xml**
   - Procesa servlets, filtros, listeners y configuraciones.

6. **Registra la aplicación en el contenedor**
   - Tomcat añade la app al contexto:
     /helloworld

7. **Inicializa el servlet principal**
   - Carga clases.
   - Prepara el ClassLoader.
   - Inicia el ciclo de vida de la aplicación.

8. **La aplicación queda disponible**
   - Se puede acceder desde:
     http://localhost:8080/helloworld/


# 🧪 4. VERIFICAR QUE EL DESPLIEGUE FUE CORRECTO

Listar la carpeta desplegada:

ls /var/lib/tomcat10/webapps/helloworld/

Ver logs del despliegue:

sudo tail -f /var/lib/tomcat10/logs/catalina.out


# 🎉 5. ACCEDER A LA APLICACIÓN

Abrir en navegador:

http://localhost:8080/helloworld/


# CAPTURA DE DEMOSTRACION
![tomcat.png](/imagenes4/tomcat.png)
