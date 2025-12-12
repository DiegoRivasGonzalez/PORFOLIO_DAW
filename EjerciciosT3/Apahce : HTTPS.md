# Apache HTTPS

## Introducción
HTTPS (HyperText Transfer Protocol Secure) es la versión segura de HTTP.

Utiliza el protocolo SSL/TLS para cifrar la comunicación entre el cliente (navegador) y el servidor web.

El cifrado garantiza:

- **Confidencialidad:** los datos transmitidos no pueden ser leídos por terceros.  
- **Integridad:** evita que los datos se alteren durante la transmisión.  
- **Autenticación:** el certificado SSL/TLS asegura que el usuario se conecta al servidor legítimo.

Importancia de HTTPS:

- Protege contra ataques "man-in-the-middle".
- Aumenta la confianza del usuario.
- Es necesario para APIs seguras, OAuth y HTTP/2.
- Mejora el posicionamiento SEO.

---

## Tipos de certificados SSL/TLS

### Certificado autofirmado
Generado por el propio administrador del servidor.

**Ventajas:**
- Gratuito y rápido de generar.
- Útil en entornos de pruebas.

**Desventajas:**
- Los navegadores muestran advertencias de seguridad.
- No recomendable para producción.

---

### Certificado emitido por una CA confiable
Firmado por una Autoridad de Certificación (CA).

**Ventajas:**
- Reconocido automáticamente por navegadores.
- Aumenta la confianza del usuario.

**Tipos:**
- **DV (Domain Validation)**
- **OV (Organization Validation)**
- **EV (Extended Validation)**

Let's Encrypt ofrece certificados gratuitos y automatizados.

---

## Ejecución técnica HTTPS
Habilitamos módulos SSL y headers y comprobamos el estado.

![imagen1.jpg](/imagenesHTTPS/imagen1.png)

---

## Generar certificados SSL/TLS

### Opción A
Creamos un certificado automático con el siguiente comando y rellenamos la información solicitada.

![imagen2.jpg](/imagenesHTTPS/imagen2.png)

---

## Configurar VirtualHost en puerto 443
Creamos el fichero `ssl.conf` si no existe y añadimos las siguientes líneas:

![imagen3.jpg](/imagenesHTTPS/imagen3.png)

Luego lo habilitamos:

```
sudo a2ensite ssl.conf
```

Editamos el archivo `.conf` y añadimos `ServerName` y `Redirect`.

![imagen4.jpg](/imagenesHTTPS/imagen4.png)

Reiniciamos Apache y comprobamos el estado:

![imagen5.jpg](/imagenesHTTPS/imagen5.png)

---

## Comprobaciones
Al escribir en el navegador:

```
localhost
```

Aparece nuestra página index.

![imagen6.jpg](/imagenesHTTPS/imagen6.png)

También comprobamos por consola con:

```
curl -I https://localhost
```

Y obtenemos:

```
HTTP/1.1 200 OK
```
![imagen7.jpg](/imagenesHTTPS/imagen7.png)

---

## Conclusión
- Apache no arrancaba al principio porque las rutas de los certificados no coincidían con los nombres correctos.
- También hubo confusión al usar `index.html` como `ServerName` en vez de `localhost`.
- Tras corregirlo, la configuración pasó `apachectl configtest` sin errores.
- El navegador muestra advertencias por tratarse de un certificado autofirmado.
- La redirección HTTP → HTTPS funciona correctamente.
- El archivo `index.html` se sirve correctamente tanto en navegador como en `curl`.

