# HERRAMIENTAS DE TRABAJO
## ¿Qué es GIT?

**Sistema de control de versiones**. Podemos ver un histórico muy detallado de las versiones y podemos regresionar a esas versiones.

**Sistema de colaboración eficiente**: facilita el trabajo en equipo.

**Permite la ramificación (branch)**: podemos trabajar sin tener que afectar a la rama main. Facilitando metodologías como GitFlow.

Es **distribuido** y **descentralizado**: cada desarrollador tiene copia completa y cuando quiera subir los cambio puede hacerlo.
## Estados
* **Modificado (modified)**: el archivo ha sido modificado desde la última confirmación.
* **Preparado (staged)**: se marcan los cambios para guardarlos (git add).
* **Confirmado (committed)**: confirmamos los cambio marcados (git commit).
## GIT FLOW
No es la única de las metodologías sobre Git que podemos utilizar, pero si la más extendida.

[Estrategias de branching](https://openwebinars.net/blog/estrategias-de-branching-gitflow-gitlab-flow-oneflow-github-flow/)

### Organización de ramas
* **Main**: principal.
*	**Develop**: rama de desarrollo. Para implementar una novedad, luego irá a Main o no.
*	**Feature**: preparada para añadir las novedades. Si quisiera añadir una sección de noticias a mi web, se crearía aquí para posteriormente unirla a la rama Develop.
* **Release**: preparada para publicar los cambios. Dónde se genera la versión.
*	**Hotfix**: específica para crear parches críticos.
### Ventajas de Git sobre otros sistemas de control de versiones
* **CVS (Concurrent Versions System)**
  * *Descentralización*: Git es descentralizado, lo que significa que no hay un único repositorio central. Cada usuario tiene una copia local completa del repositorio.
  * *Velocidad*: Las operaciones en Git son generalmente más rápidas que en CVS debido a su diseño optimizado y su uso de almacenamiento local.
*	**SVN (Subversion)**
  * *Descentralización*: Al igual que CVS, SVN tiene un repositorio centralizado, mientras que Git es descentralizado. Esto permite una mayor flexibilidad en el trabajo colaborativo y una mejor gestión de ramas.
  * *Ramas más eficientes*: Git maneja ramas de forma más eficiente que SVN, lo que facilita el trabajo en paralelo y la integración de cambios.
* **Mercurial**
  * *Velocidad*: Git tiende a ser más rápido que Mercurial en muchas operaciones, especialmente en proyectos grandes con historias largas.
  * *Herramientas y comunidad*: Git tiene una comunidad más grande y una gama más amplia de herramientas y servicios de alojamiento de repositorios, lo que facilita la colaboración y la integración con otras herramientas de desarrollo.
* **Monotone**
  * *Rendimiento*: Git tiende a ser más rápido que Monotone, especialmente en proyectos grandes con historias largas.
  * *Distribución*: Git ofrece una mejor distribución de los cambios y un sistema de ramificación más flexible, lo que facilita el trabajo colaborativo en equipos distribuidos.
## Software de trabajo
### Git
Enlace de descarga [aquí](https://git-scm.com/).
Particularidades:
En Windows podemos integrar con el explorador con:
![image](https://github.com/eguirod/git/assets/71733548/1967ebb3-b768-4173-bee0-ef84940d7025)
Git LFS, para tratar con archivos grandes.
![image](https://github.com/eguirod/git/assets/71733548/4a6b152e-7d96-4d95-8f60-1b9cfbab3eee)
Añadir Git Bash a la terminal de Windos
![image](https://github.com/eguirod/git/assets/71733548/d9705826-0b06-4ad4-b042-f0f5245bd511)
Para elegir qué programa vamos a usar para editar los ficheros:
![image](https://github.com/eguirod/git/assets/71733548/338cd8de-6e62-4e49-b3be-d955c95eeeef)
Para elegir el nombre de la rama main.
![image](https://github.com/eguirod/git/assets/71733548/768c2e20-07c0-4304-aa1f-34a3a10c1774)
Elegir el entorno de PATH (específico de Windows):
![image](https://github.com/eguirod/git/assets/71733548/bfff0921-eadb-4ea5-9bcc-335da0af2ba4)
**Punto crítico**, conocer qué usa Windows como salto de línea: la primera opción es la más recomendable, ya que cuando descargo el código usa los saltos de líneas de Windows y cuando suba transforma los saltos de líneas en estilo Linux.
![image](https://github.com/eguirod/git/assets/71733548/c155c5ad-a023-450c-82db-dc15c91e5e75)
