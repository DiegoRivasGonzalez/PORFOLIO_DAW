# Funcionalidades de GitHub 
_Diego Rivas Gonzalez_
## ¿Que es GitHub?
GitHub es una plataforma web en la nube para alojar código y colaborar en proyectos de desarrollo de software, utilizando el sistema de control de versiones Git. Permite a los desarrolladores almacenar su trabajo en "repositorios", gestionar los cambios a lo largo del tiempo, compartir su código, y trabajar en equipo con otros, incluso a través de una interfaz de usuario simplificada que facilita el uso de Git.
### ¿Que es Git?
Git es un sistema de control de versiones distribuido (DVCS) de código abierto que permite a los desarrolladores rastrear y gestionar los cambios en el código de un proyecto, colaborar eficazmente y mantener un historial de versiones completo y seguro. Funciona tomando "instantáneas" del proyecto en cada cambio (conocidas como **commits**), creando ramas para trabajar de forma aislada y luego fusionando esas ramas en el proyecto principal.
### Que se va a ver en este informe
En este informe veremos desde cero como empezar a utilizar la herramienta de GitHub desde crear la cuenta hasta hacer **commits** y fusionar ramas.
## Como empezar en GitHub
Lo primero de todo sera crear una cuenta en [GitHub](https://github.com/).
![Login](/Imagenes/InicioSesion.png)
Una vez dentro vemos en la pantalla principal que tenemos la opción de crear repositorios.
![CrearRepositorios](/Imagenes/CrearNuevoRepositorio.png)
Una vez en esta pagina podemos poner el nombre de nuestro repositorio, si es publico y mas opciones.
![CrearElRepositorio](/Imagenes/CrearElRepositorio.png)
Una vez creado podemos emepezar a subir archivos de todo tipo para nuestros trabajos o proyectos
![PaginaPrincipalDelRepositorio](/Imagenes/PaginaPrincipalDelRepositorio.png)
## Subir archivos y visualizar contenidos
En la pestaña principal del repostorio pulsamos en el siguiente boton para subir archivos.\
![SubirArchivo.png](/Imagenes/SubirArchivo.png)\
Ahora podemos elegir el archivo que queremos subir, decir a que rama queremos que vaya y darle un nombre y descripción al archivo.\
![ArchivoSubido.png](/Imagenes/ArchivoSubido.png)\
Con el archivo subido al repositorio en la pestaña principal podemos seleccionar cual queremos visualizar.\
![VerArchivo](/Imagenes/VerArchivo.png)\
Dentro tendremos la opción de ver a que rama pertenece ver el codigo o como queda con una preview y ver la descripción del archivo.\
![VisualizarContenido](/Imagenes/VisualizarContenido.png)\
## Commits
Un commit sucede cada vez que subimos un archivo o cambiamos el contenido del mismo. Los commits realizados a lo largo de un proyecto se pueden ver en la pestaña conocida como **Historial de Commits** en la que encontramos toda la información.\
![HistorialdeCommits](/Imagenes/HistorialCommits.png)\
## Funcionamiento de las Ramas
Las ramas son lo que nos ayudara a modificar proyectos sin miedo a empeorar lo que ya funcionaba antes por que crea un archivo "distinto" pero con el mismo codigo que no afecta en nada al codigo principal.\
Para crear una nueva rama seleccionamos el icono arriba a la derecha donde aparece el icono de las ramas y el nombre de la rama en la que estas y dentro creamos una nueva rama desde el main y le damos nombre.\
![CrearNuevaRama](/Imagenes/CrearNuevaRama.png)\
Con la nueva rama creada podemos subir archivos a esa rama para que no afecte a la principal.\
![ArchivoRamaSecundaria](/Imagenes/ArchivoSubidoRamaSecundaria.png)\
### Fusionar ramas
Tenemos una pestaña llamada pull request dodne podemos fusionar las ramas para que los cambios se produzcan en el main.\
![FusionarRamas](/Imagenes/FusionarRamas.png)\
Despues de pulsar en el boton new pull request nos dara la opción de seleccionar las ramas que queremos fusionar y solo tendremos que elegir dos y pulsar en create pull request.\
![SeleccionarRamas](/Imagenes/SeleccionarRamas.png)\
Ahora tendremos que hacer el merge para confirmar los cambios despues de comprobar que no hay ningun conflicto al fusionar las ramas.\
![HacerMerge](/Imagenes/HacerMerge.png)\
Una vez terminado vamos a la pestaña principal y vemos que en el main tenemos el archivo de prueba de la rama 2.\
![VisionarRamasUnidas](/Imagenes/VisionarRamasUnidas.png)\
## Pestaña de Settings
Pulsando en los tres puntitos de arriba a la derecha tenemos la pestaña de settings.\
![Settings.png](/Imagenes/Settings.png)\
En esta pestaña de un repositorio en GitHub es donde puedes configurar prácticamente todos los aspectos importantes de ese proyecto. Lo que aparece puede variar según si eres el dueño, colaborador o miembro, pero en general ahí puedes cambiar el nombre del repositorio, editar la descripción y la URL del proyecto, administrar colaboradores como añadir o eliminar personas con acceso y demas opciones.\
![PantallaDeSettings](/Imagenes/PantallaDeSettings.png)
