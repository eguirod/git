# HERRAMIENTAS DE TRABAJO
## ¿Qué es GIT?
**Sistema de control de versiones**. Podemos ver un histórico muy detallado de las versiones y podemos regresionar a esas versiones.
**Sistema de colaboración eficiente**: facilita el trabajo en equipo.
**Permite la ramificación (branch)**: podemos trabajar sin tener que afectar a la rama main. Facilitando metodologías como GitFlow.
Es **distribuido** y **descentralizado**: cada desarrollador tiene copia completa y cuando quiera subir los cambio puede hacerlo.
## Estados
Modificado (modified): el archivo ha sido modificado desde la última confirmación.
•	Preparado (staged): se marcan los cambios para guardarlos (git add).
•	Confirmado (committed): confirmamos los cambio marcados (git commit).
GIT FLOW
No es la única de las metodologías sobre Git que podemos utilizar, pero si la más extendida.
Artículo pendiente de leer aquí.
Organización de ramas
•	Main: principal.
•	Develop: rama de desarrollo. Para implementar una novedad, luego irá a Main o no.
•	Feature: preparada para añadir las novedades. Si quisiera añadir una sección de noticias a mi web, se crearía aquí para posteriormente unirla a la rama Develop.
•	Release: preparada para publicar los cambios. Dónde se genera la versión.
•	Hotfix: específica para crear parches críticos.
Ventajas de Git sobre otros sistemas de control de versiones
•	CVS (Concurrent Versions System) 
o	Descentralización: Git es descentralizado, lo que significa que no hay un único repositorio central. Cada usuario tiene una copia local completa del repositorio.
o	Velocidad: Las operaciones en Git son generalmente más rápidas que en CVS debido a su diseño optimizado y su uso de almacenamiento local.
•	SVN (Subversion) 
o	Descentralización: Al igual que CVS, SVN tiene un repositorio centralizado, mientras que Git es descentralizado. Esto permite una mayor flexibilidad en el trabajo colaborativo y una mejor gestión de ramas.
o	Ramas más eficientes: Git maneja ramas de forma más eficiente que SVN, lo que facilita el trabajo en paralelo y la integración de cambios.



•	Mercurial 
o	Velocidad: Git tiende a ser más rápido que Mercurial en muchas operaciones, especialmente en proyectos grandes con historias largas.
o	Herramientas y comunidad: Git tiene una comunidad más grande y una gama más amplia de herramientas y servicios de alojamiento de repositorios, lo que facilita la colaboración y la integración con otras herramientas de desarrollo.
•	Monotone 
o	Rendimiento: Git tiende a ser más rápido que Monotone, especialmente en proyectos grandes con historias largas.
o	Distribución: Git ofrece una mejor distribución de los cambios y un sistema de ramificación más flexible, lo que facilita el trabajo colaborativo en equipos distribuidos.
Software de trabajo
Git
Enlace de descarga aquí.
Particularidades:
En Windows podemos integrar con el explorador con:
