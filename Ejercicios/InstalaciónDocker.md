# Rivas González Diego – Virtualización  
**Diego Rivas González 2ºDAW**

---

## Generadores de Documentación  
**Diego Rivas González**  
**2º DAW**

---

## INSTALACIÓN DOCKER-DESKTOP  

Lo primero será actualizar el sistema para tener todo listo y evitar fallos.

![imagen1](imagen1.png)

Instalamos los paquetes requeridos para docker.

![imagen2](imagen2.png)

Instalamos el **docker engine**, la interfaz de línea de comandos, el runtime y los plugins para **docker compose**.

![imagen3](imagen3.png)

---

## COMPROBAR ESTADO DOCKER  

Comprobamos el estado de docker y vemos que está activo y funcionando.

![imagen4](imagen4.png)

---

## UTILIZAR DOCKER SIN SUDO  

Al hacer este comando vemos que no funciona sin utilizar `sudo`.  
Para que funcione vamos a hacer lo siguiente:

![imagen5](imagen5.png)

Damos permisos al usuario y reiniciamos.

![imagen6](imagen6.png)

Y hacemos el comando sin `sudo` para ver que funciona correctamente.

![imagen7](imagen7.png)

---

## INSTALACIÓN DE CONTENEDORES DE SERVIDOR WEB Y APLICACIONES  

Buscaremos la imagen del servidor web que será **Nginx** con este comando.

![imagen8](imagen8.png)

Y el de aplicaciones que será **Tomcat**.

![imagen9](imagen9.png)

---

## INICIAR CONTENEDORES  

Después iniciaremos los contenedores con estos comandos.

![imagen10](imagen10.png)

---

## VERIFICAR ESTADO  

Verificamos que están activos.

![imagen11](imagen11.png)

---

## COMPROBAR EN NAVEGADOR  

Y comprobamos en un navegador.

![imagen12](imagen12.png)
![imagen13](imagen13.png)
![imagen14](imagen14.png)
![imagen15](imagen15.png)

---

## RESULTADOS  

Se verifica que ambos contenedores están en ejecución:  
- **Nginx** (servidor web) en el puerto 8080  
- **Tomcat** (servidor de aplicaciones) en el puerto 8081  

Ambos muestran sus respectivas páginas al acceder desde el navegador.

![imagen16](imagen16.png)
![imagen17](imagen17.png)
![imagen18](imagen18.png)

---
