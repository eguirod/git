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

### SourceTree
* Interfaz gráfica para trabajar con GIT con todas las opciones.
* Herramienta más completa con alternativas similares como GitKraken.
* Enlace de descarga aquí.

### GitHub Desktop
Bastante utilizado por pertenecer a GitHub, pero no tiene integradas todas las opciones de Git.

### Kdiff3
* Sirve para resolver conflictos de forma visual.
* Se suele usar en entornos Windows y Linux.
* Enlace de descarga aquí.

## Introducción a GitHub y GitLab-SSH

### SSH
Protocolo de red seguro para operaciones remotas, proporciona autenticación segura y comunicaciones cifradas.

* Autenticación Clave Pública:
    * Permite acceder a repositorios Git mediante un par de claves públicas y privadas.
    * Mayor seguridad en comparación con la autenticación basada en contraseñas.
* Configuración de Claves SSH.
    * Generar un par de claves SSH: pública y privada.
    * Agregar la calve pública al servidor Git para autenticación.
* Uso con Git:
    * Configurar Git para usar SSH en lugar de HTTP/HTTPS.
    * Proporciona acceso seguro a repositorios remotos sin necesidad e ingresas credenciales cada vez.
* Configurando SSH
    * Generar un par de claves SSH: pública y privada desde una terminal:
```
ssh-keygen -t ed25519 -C “comentario”
```
  * Agregar la clave pública al servidor Git para autenticación.

![image](https://github.com/eguirod/git/assets/71733548/63918ee9-5db2-4108-a68e-d93523d7b5df)

![image](https://github.com/eguirod/git/assets/71733548/89c1fdaf-3a54-49d9-8ce9-0d14c6eb40a7)

![image](https://github.com/eguirod/git/assets/71733548/85a94ed3-c4af-4a9e-86ba-f092ec49ccd0)

![image](https://github.com/eguirod/git/assets/71733548/6c923dc3-4a31-465d-a2b2-fa4a68866c0b)

![image](https://github.com/eguirod/git/assets/71733548/b9fd6b6b-d42b-4f6a-9d8b-724b9e4e8bc6)

Para comprobar que ha ido OK, intentamos conectar con: ssh -T git@github.com y si devuelve este mensaje hemos añadido la clave correctamente.

![image](https://github.com/eguirod/git/assets/71733548/8fa31714-a427-48ab-8f4c-eee22c3f25e1)

### De RSA a Ed25519
Hasta hace poco tiempo las claves SSH se encontraban siempre en formato RSA. Sin embargo, la tendencia está cambiando e incluso GitHub y GitLab recomiendan utilizar ed25519 en la actualidad. Pero, ¿Por qué?:

* **Resistencia a ciertos ataques**: Ed25519 es menos vulnerable a ciertos tipos de ataques criptográficos, como los relacionados con la factorización de números grandes, lo que ofrece una capa adicional de seguridad.
* **Mejor rendimiento**: Ed25519 tiende a ser más eficiente que RSA en términos de generación de claves, firma y verificación de firmas. Esto es especialmente importante en entornos donde el rendimiento es crítico.
* **Claves más cortas**: Las claves Ed25519 son más cortas que las claves RSA para proporcionar un nivel de seguridad similar. Esto facilita su manejo y almacenamiento, especialmente en dispositivos con recursos limitados.

### Extra: GPG
GPG, o GNU Privacy Guard, es una herramienta de cifrado de datos de código abierto que proporciona seguridad y privacidad para la comunicación y el almacenamiento de datos. Utiliza un sistema de clave pública para cifrar y firmar mensajes, lo que permite a los usuarios proteger la confidencialidad e integridad de su información.
### Utilización con Git
GPG se utiliza en combinación con Git para firmar y verificar commits y tags, lo que añade una capa adicional de seguridad y autenticación al historial de cambios de un repositorio. Al firmar commits con GPG, se puede verificar la autenticidad del autor y garantizar que los cambios no han sido manipulados. Pensemos en que sin GPG cualquier persona puede introducir en la configuración de git sobre los datos de nombre y apellidos y correo electrónico los valores que quiera, lo que puede provocar una suplantación de identidad.
Ventajas de utilizar GPG con Git
* **Autenticación**: Permite verificar la identidad del autor de un commit.
* **Integridad**: Asegura que los commits no han sido modificados desde su creación.
* **No repudio**: Los autores no pueden negar la autoría de sus commits firmados.
* **Confianza**: Aumenta la confianza en la integridad del código fuente del repositorio.
# ORGANIZACIÓN DEL CÓDIGO FUENTE
## Creación de un repositorio local
### ¿Qué encontramos dentro de .git?
Dentro del directorio .git de un repositorio de Git, se encuentra la estructura que gestiona todos los aspectos del control de versiones y la gestión del repositorio. Directorios más importantes:
* **branches/**: Contiene archivos que mantienen información sobre las ramas del repositorio.
* **hooks/**: Almacena scripts que se ejecutan en eventos específicos, como la creación de commits o la recepción de commits remotos.
* **info/**: Contiene información adicional sobre el repositorio, como por ejemplo ficheros a ser excluidos.
* **objects/**: Almacena todos los objetos de Git, como blobs (contenido de archivos), árboles (estructura de directorios) y commits, identificados por un hash SHA-1.
* **refs/**: Contiene referencias a objetos en la base de datos de Git, incluyendo ramas, etiquetas y otras referencias.
* **config**: Almacena la configuración específica del repositorio.
* **HEAD**: Es un archivo especial que apunta a la rama actual del repositorio.
* **index**: Almacena el estado del área de preparación (staging area), donde se preparan los cambios para el próximo commit.

Esta estructura de directorios es esencial para el funcionamiento interno de Git y proporciona los componentes necesarios para gestionar eficientemente el control de versiones.
## Aprobación de cambios en consola
### ¿Por qué temenos un staging area?
El concepto de un **“staging area”** en Git proporciona una funcionalidad importante que ayuda a mantener un control preciso sobre los cambios que se incluirán en un commit. Aquí están algunas razones por las que el staging area es útil y por qué separarlo del commit area:
* **Revisión antes del commit**: El staging area permite revisar los cambios antes de confirmarlos definitivamente en un commit. Esto proporciona una oportunidad para revisar los cambios realizados y asegurarse de que solo se incluyan los cambios deseados en el próximo commit.
* **División lógica de cambios**: Con el staging area, puedes dividir tus cambios en commits lógicos y separados. Esto es útil para mantener un historial de cambios limpio y comprensible, ya que cada commit puede representar una unidad coherente de trabajo.
* **Control granular**: El staging area brinda un control granular sobre los cambios que se incluirán en un commit. Puedes agregar, eliminar o modificar archivos en el staging area según sea necesario antes de realizar el commit, lo que te permite ajustar tu commit según lo requiera tu flujo de trabajo.
* **Prevención de commits accidentales**: Separar el staging area del commit area ayuda a prevenir commits accidentales. Antes de confirmar cambios, debes ser explícito al agregar archivos al staging area, lo que te da una oportunidad para revisar los cambios y evitar errores antes de que se incorporen al historial de versiones.

Para evitar que haya archivos que se incluyan en el commit Podemos crear un fichero llamado .gitignore en el que indicaremos lo que no queremos que suba con expresiones regulares.

Existe un gitignore_global en el que Podemos añadir lo que no queremos que se incluya en ningún Proyecto.
## Trabajar en remoto
Para ello temenos que usar una plataforma de git remota, gitlab o github.
## Deshaciendo cambios
###Deshaciendo en Working area
Esto nos revierte el fichero a la versión HEAD (es decir, el commit en el que estamos posicionados)
```git checkout -- nombre_del_archivo```
### Deshaciendo en Staging area
Si nuestros cambios ya están en staging area tendremos que apoyarnos en git reset indicando a dónde queremos volver (normalmente HEAD)
```git reset HEAD nombre_del_archivo```
### Deshaciendo Commits
Nuevamente, podemos hacer uso de git reset para deshacer commits, pero debemos de tener presente que en este punto se vuelve peligroso, es una operación destructiva que puede eliminar commits
```git
# Deshacer el último commit manteniendo los cambios en el staging area
git reset --soft HEAD~1
# Deshacer el último commit y quitar los cambios del staging area (los mantiene en Working area)
git reset --mixed HEAD~1
# Deshacer los últimos dos commit y eliminar los cambios. OJO, eliminaremos commits!
git reset --hard HEAD~2
```
Existe un método alternativo para deshacer commits menos destructivo. git revert. Con este comando crearemos un commit nuevo que deshace los cambios del commit al que apuntemos, por lo que el resultado final en el código es equivalente, pero mantenemos la trazabilidad en los commits para entender mejor qué ocurrió.

Lo único que tenemos que tener en cuenta cuando utilizamos git revert es que si revertimos un commit cuyo contenido ha sido cambiado posteriormente nos encontraremos con conflictos de fusión que deberemos resolver.
```git
# Deshacer el último commit con un nuevo commit
git revert HEAD
# Deshacer el penúltimo commit con un nuevo commit
git revert HEAD^
# Deshacer el commit 3489ef2 con un nuevo commit
git revert 3489ef2
```
### Resolviendo conflictos
Normalmente nos encontramos conflictos cuando hacemos merge de diferentes ramas, pero también pueden dares al hacer un git revert.
### Subiendo cambios
```git
git push [remote]
# Comprobar nuevos cambios
git fetch
# Bajar cabios desde el servidor
git pull
```
# FLUJOS DE TRABAJO
## Encontrando errores
### Git diff
Es un comando utilizado en Git para mostrar las diferencias entre los cambios en el área de trabajo (working directory) y el área de preparación (staging area), entre el área de preparación y la última confirmación (commit), o entre dos commits arbitrarios. Muestra las diferencias en un formato legible para el usuario, con líneas que comienzan con símbolos + para adiciones y - para eliminaciones. También puede mostrar líneas contextuales para proporcionar una mejor comprensión del contexto de los cambios. Principales usos:
* Diferencias entre el área de trabajo y el área de preparación: Muestra las diferencias entre los archivos en el área de trabajo (los cambios que no han sido preparados) y el área de preparación (los cambios que se han preparado pero aún no se han confirmado).
```git diff```
* Diferencias entre el área de preparación y el último commit: Muestra las diferencias entre los archivos en el área de preparación y el último commit confirmado.
```git diff --staged o git diff --cached```
* Diferencias entre dos commits: Muestra las diferencias entre dos commits específicos. Puedes especificar los commits usando sus hashes, nombres de ramas, o referencias de etiquetas.
```git diff commit1 commit2```
* Vista previa de cambios antes de confirmar: Útil para revisar los cambios que se prepararán para la próxima confirmación antes de realizar la confirmación.
```git diff --cached (o git diff --staged)```
* Comparación de ramas: Muestra las diferencias entre dos ramas diferentes.
```git diff branch1 branch2```
* Comparación de etiquetas: Muestra las diferencias entre dos etiquetas diferentes.
```git diff etiqueta1 etiqueta2```
### Git log
Puedes utilizar git log para encontrar errores en tu código de varias formas:
* Buscar commits que introdujeron cambios: Utiliza git log para revisar los commits recientes y encontrar aquellos que introdujeron cambios problemáticos. Puedes usar opciones como --oneline para obtener una vista simplificada de los commits y --grep para buscar mensajes de commit específicos relacionados con errores.
```git log --oneline --grep="Texto en el commit"```
* Revisar cambios en un archivo específico: Si tienes un archivo en particular con errores, puedes utilizar git log para revisar su historial y encontrar los commits que lo modificaron. Esto puede proporcionar contexto sobre los cambios que pueden haber introducido errores.
```git log --oneline -- fichero_a_revisar.txt```
* Utilizar Opciones de Visualización Avanzada: tiene varias opciones de visualización que te permiten ver detalles específicos sobre los commits, como los cambios introducidos en cada uno. Puedes usar git log -p para mostrar los parches introducidos en cada commit y git log --stat para ver estadísticas resumidas de los cambios.
```git log -p```
## Git Blame
Es un comando que muestra quién modificó por última vez cada línea de un archivo, junto con el hash del commit que introdujo el cambio y la fecha en que se realizó ese commit. Este comando es útil para rastrear la historia de un archivo y entender quién contribuyó a qué partes del mismo. Algunos de los usos comunes de git blame incluyen:
* Entender la autoría del código: Permite identificar quién escribió cada parte de un archivo, lo que puede ser útil para entender el contexto detrás de un cambio específico.
* Rastrear responsabilidades: Ayuda a asignar responsabilidades y aclarar dudas sobre por qué ciertas partes del código fueron modificadas.
* Depuración y mantenimiento: Facilita la depuración de problemas o errores al proporcionar información sobre quién realizó cambios en ciertas líneas de código.
* Revisión de código: Es útil durante la revisión de código para comprender el historial y el propósito de cambios específicos.
  
El comando se usa típicamente de la siguiente manera:
```git blame nombre_del_archivo```
## Estrategia Merge
Se utiliza para fusionar los cambios de una rama en otra. Cuando ejecutas git merge, Git combina los cambios realizados en la rama especificada con la rama actual y crea un nuevo commit de fusión. Esto significa que se crea un nuevo commit que integra los cambios de ambas ramas.

Por ejemplo, si estás en la rama master y quieres fusionar los cambios de la rama feature, puedes hacerlo así:
```git
git checkout master
git merge feature
```
Esto fusionará los cambios de la rama feature en la rama master moviendo la referencia de la rama hacia adelante en línea recta sin crear un commit de fusión adicional, a menos que existieran conflictos de fusión.

### Git Merge sin Fast-Forward
El argumento --no-ff (“no fast-forward”) se utiliza junto con git merge para forzar la creación de un commit de fusión incluso si Git podría realizar una fusión “fast-forward” de manera automática.

Sin embargo, en algunos casos, puede ser útil tener un commit de fusión explícito incluso si no hay conflictos. Esto proporciona una mejor historia del proyecto al conservar la información sobre cuándo se integraron las ramas. Para lograr esto, se usa --no-ff.

Por ejemplo:
```git
git checkout master
git merge --no-ff feature
```
Esto fusionará los cambios de la rama feature en la rama master, creando un nuevo commit de fusión incluso si no hay conflictos entre las ramas.
### Para los cafeteros: git merge avanzado
git merge es un comando más complejo de lo que parece, y puede llegar a combinar cambios de formas muy diversas. Aquí tenemos un pequeño resumen de la capacidad de git merge con diferentes estrategias para la gente con más curiosidad (esto queda fuera de los contenidos del curso, es algo avanzado):
**Recursive**
```git merge -s recursive branch1 branch2```
Esta estrategia actúa en dos heads. Recursive es la estrategia de fusión predeterminada a la hora de incorporar cambios de una rama o fusionarla. Además, permite detectar y manejar fusiones que implican cambios de nombre, aunque actualmente no puede usar copias detectadas. Se trata de la estrategia de fusión predeterminada a la hora de incorporar cambios de una rama o fusionarla.
**Resolve**
```git merge -s resolve branch1 branch2```
Esta estrategia solo permite resolver dos heads usando un algoritmo de fusión a 3 vías. Trata de detectar minuciosamente las ambigüedades de fusión entrecruzada y se la suele considerar una estrategia segura y rápida.
**Octopus**
```git merge -s octopus branch1 branch2 branch3 branchN```
Se trata de la estrategia de fusión predeterminada para más de dos heads. Cuando te mueves por más de una rama, Octopus se activa automáticamente. Si una fusión tiene conflictos que requieren una resolución manual, Octopus rechazará el intento de fusión. Se utiliza principalmente para agrupar heads de rama de función similares.
**Ours**
```git merge -s ours branch1 branch2 branchN```
Esta estrategia actúa en varios números N de ramas. El resultado de la fusión de salida es siempre el del HEAD de la rama actual. El término “ours” implica la preferencia ignorando efectivamente los cambios de todas las demás ramas. Está diseñado para combinar el historial de ramas de función similares.
**Subtree**
```git merge -s subtree branchA branchB```
Se trata de una extensión de la estrategia recursiva. Al fusionar A y B, si B es un subárbol secundario de A, B se actualiza en primer lugar para reflejar la estructura de árbol de A. Esta actualización también se realiza en el árbol antecesor común compartido entre A y B.
## Estrategia Rebase
Busca la conversión del código, pero reescribiendo la o las ramas quedando todo mucho más limpio.
## Estrategia Merge Squash-Rebase
## Git stash
Funcionalidad que nos permite almacenar cambios en un cajón.
## Saltando entre commits
# TRABAJO COLABORATIVO
## Etiquetas
Punto específico de la historia dentro de nuestro repositorio git, que nos permite seguir un sistema de versionado semántico en el que el primer número corresponde a una versión mayor, el segundo a una menor y el último una versión de parche.

También es muy útil para marcar hitos dentro de nuestro proyecto/app desde el que hacer un despliegue en producción.

Se pueden expandir añadiendo más información, es lo que se conoce como Release.
```git tag nombre_etiqueta```
Para subir las etiquetas a github o gitlab desde terminal:
```git push origin –tags```
Para crearla desde Sourcetree simplemente hacemos clic derecho en el commit y damos en Tag… y rellenar los campos.
## Releases
Son una extensión de los tags que tenemos en git vitaminada.

Desde GitHub podemos ir a las Tags, accedemos a la propia etiqueta y picamos en la opción Create release from tag.
Permite añadir un título y una descripción más extensa de los cambios. También se puede añadir una Releases notes que permita indicar qué cambios ha habido entre la versión anterior y la nueva, mejoras… inclusive añadir binarios, imágenes…

En GitLab encontramos lo mismo.
## Issues
Son las Incidencias que nos permite mejorar en nuestro trabajo colaborativo.

Permite informar sobre fallos que encontramos, sugerencia de mejoras… permitiendo enlazarlo con el Código que desarrollamos.

En GitHub, cuando se genera una issue se genera automáticamente un identificador que es lo que nos permite enlazar el Código con las issues, creando una rama en features hacienda referencia a ese ticket y en el commit haríamos referencia al ticket escribiendo #1.

En GitLab es similar a GitHub.

En ambos clientes se pueden generar plantillas.
## Pull Requests
Una vez hemos terminado nuestro commit y queremos que nuestros cambios se integren en la página principal creamos una pull request, que no es más que una petición para que nuestro código suba a la rama que deseemos, que deberá ser aprobado por la persona asignada.
## Integración continua
Podemos automatizar rutinas, como pasar test unitarios que hayamos incluido en el código, comprobar si hay dependencias antiguas o posibles fallos de código… incluso realizar un despliegue en Docker u otro servicio parecido.

En caso de GitHub creamos un directorio llamado .github/workflows y dentro de él un fichero yml en el que especificamos qué queremos que ocurra cunado realicemos una subida.

En GitHub se llaman Actions, en GitLab Pipelines.

En GitLab crearemos un .gitlab-ci.yml en la raíz del proyecto.

Cuando hagamos una pull request si no pasa los test no se podrá aprobar la pull request.

