# GITFLOW

## Introducción

GitFlow es un modelo de branching que propone una estrategia de ramificación y de generación 
de versiones de productos usando un repositorio GIT. Ayuda a los equipos a asegurar la calidad
 del código y la eficiencia en la integración en equipos de más de un miembro.

### Descentralizado pero Centralizado

Como dijo Vincent Driessen, GIT ha revolucionado la forma de hacer software. Antes con SVN o 
CVS los merges daban un poco de miedo, ya que los conflictos se generaban en el único 
repositorio que tienen, el remoto, y directamente sobre el trunk. Eso hace los conflictos 
extensibles a todos los miembros del equipo y además se generan directamente sobre la rama
 principal. Digamos que no favorece mucho el branching y en trabajo colaborativo, sin embargo,
 con git es extremadamente fácil, al contar con el repositorio local.

Por eso decimos que con git-flow partimos de un repositorio centralizado, pero que a la vez es
 descentralizado. Esto se debe a que todos tenemos nuestro repositorio local, como hemos 
 comentado, pero a su vez apuntamos a un repositorio remoto llamado “origin”. Toda la 
 comunicación entre los desarrolladores tiene que pasar por origin y no de un desarrollador a
 otro, lo que refleja todos los cambios que hace cada uno y les permite integrar código en sus
 repositorios locales y detectar conflictos de forma temprana.

<img width="419" alt="gitFlow" src="https://github.com/eguirod/git/assets/71733548/04d8ea96-9a83-4772-b606-cf81628464a3">

## Flujo de trabajo

### Dos tipos de ramas

GitFlow define dos tipos de ramas, las **principales** y las **auxiliares**.
Las principales diferencias entre estos dos grupos de ellas son:
* Ramas Principales (*master* y *develop*):
	* No se pueden instanciar.
	* Su nombre no tiene complementos, se llaman master y develop “a secas”.
	* No se puede commitear código directamente sobre ella, para no perder el control de los cambios, solo recibe merges de otras ramas.
* Ramas Auxiliares (*feature*, *release* y *hotfix*):
	* Se pueden instanciar tantas veces como características, versiones y defectos haya. No hay límite.
	* Su nombre consta de una raíz, que corresponde al tipo de rama, más la característica implementada o versión. Este complemento la hace inconfundible. Por ejemplo feature-67432-alta-usuario.
	* El objetivo es trabajar directamente sobre ella, subiendo código código a la rama. Luego se mergea con las ramas principales.

### Master

La rama master es la rama principal del repositorio y contiene el código que está actualmente 
en producción o próximo a subir en una situación estable.
No se hace commit de código de ella, salvo circunstancias muy especiales y por alguien con 
altos conocimientos en el producto.
Por regla general, recibe **merges** de ramas **release** o **hotfix**. En esta rama están 
etiquetadas todas las versiones del producto.

### Develop

La rama develop es la rama principal del repositorio que contiene, además del contenido de
 master, características desarrolladas que aún no están en producción.
En esta rama se está desarrollando código de forma continua, eso sí, todo el contenido que
 recibe a través de merges de ramas features principalmente, está testeado y verificado, por
 lo que es código estable.
No se hace commit de código de ella, salvo circunstancias muy especiales, al igual que en la
 rama master.
El principal objetivo de esta rama es evitar conflictos es master, por lo que el código se
 depura en esta rama primero.
No se crea por defecto. Cuando tenemos instalado gitflow y hacemos ```gitflow init``` si se
 crea.
Se genera a partir de master y al igual que en master no se debe hacer commit en ella.
Solo hay un develop.
Contiene el código que aún no está en PRO pero con calidad, completo y funcional.
Recibe código de otras ramas.
Mantiene master limpio y evitando conflictos.
Aquí siempre habrá un desarrollo continuo, por eso habrá diferencias entre master y develop.

### Feature

Cada vez que se va a desarrollar una nueva funcionalidad o modificar una existente, se genera
 una rama de tipo feature, a partir de develop, cuyo nombre está formado por esta palabra y
 por la característica a implementar, por ejemplo: “feature/nueva-interfaz”.
Sobre ella se sube el código a través de commits del equipo que debe ser probado antes de
 mergear con develop, por lo que durante este proceso hay una funcionalidad en curso
 codificándose, pudiendo trabajar varios miembros a la vez en ella.
Una buena práctica es hacerlas lo más atómicas posibles, pudiendo generar más de una para
 cubrir una característica y mergeando código de unas a otras.
Su gestión depende del acuerdo interno del equipo/proyecto, por ejemplo una feature por
 característica, feature por cada ticket de Jira, feature por requisito o feature por tarea.
Se generan para desarrollos cortos, no deben eternizarse.
Pueden tener JUnits, scripts de rendimiento, calidad, automatización...
Al final del sprint todas las features que estén finalizados y mergeados en develop serían los
 candidatos a pasar a master.

### Release

Estas ramas se generan cuando quiere realizarse la tentativa de entrega de una versión,
 habitualmente cuando se aproxima la finalización de un sprint.
Esto congela los desarrollos, que prosiguen en develop, y agrupa una serie de nuevas
 características en la nueva rama release, que puede llamarse, por ejemplo: “release/v2.2.0”.
Sobre ella pueden realizarse pequeños cambios, corrección de defectos, establecer versiones de
 producto… pero no desarrollar nuevas características. Una vez finalizado y testeado, se
 mergea con master (debiendo etiquetarla), como nueva versión que es candidata a subir a producción; y con develop,
 ya que hay defectos corregidos que deben volcarse a la rama de desarrollo.
Muy parecidas a las ramas hotfix.
Nos permite no parar el desarrollo mientras se hacen pruebas y corregir pequeños cambios que se
 requieran.

### Hotfix

Estas ramas se generan habitualmente cuando se detecta un defecto en producción que debe ser
 corregido con agilidad. Para ello se genera una rama de tipo hotfix, que parte del código
 existente en master.
Sobre ella pueden realizarse las correcciones que sean necesarias para arreglar el bug, para
 luego volver a mergear con master, añadiéndole un nuevo tag de versión.
También es necesario mergear con develop para que el defecto también quede corregido en
 desarrollo y si hubiera una release preparada, también se vuelva en la release en cuestión.
 
### Uniéndolo todo

Uniéndolo todo, el proceso cobra sentido, y todos los tipos de ramas se complementan los unos
 a los otros para alcanzar los objetivos que propone GitFlow.
 
### Adaptándolo a nuestro entorno

Ejemplos de entornos:
* Entorno A: aparte de la rama develop hay una rama qa para las pruebas automáticas.
* Entorno B: se elimina la rama develop quedando cubierta por master.
* Equipo pequeño (4-5 personas): solo existen ramas master y features.
 
## Comandos

### Introducción

GitFlow también es una librería que dispone de una serie de comandos git de alto nivel que se
 simplifica el uso de los comandos originales y lo adaptan al flujo de trabajo propuesto
 anteriormente.
Aun así, hay puristas que prefieren utilizar los comandos originales para sentir más el
 control sobre el repositorio.
Ventajas:
* Proporciona una serie de comandos que ayuda a gestionar el flujo.
* Muy fácil de usar.
* Está soportado por muchos GUI de Git, como Sourcetree de Atlassian.
Inconvenientes:
* Hay gente que prefiere utilizar comandos clásicos de Git.
* A veces pierdes el foto de qué ocurre "por debajo".
* Hay que usar gitflow literalmente como se pensó, con todas sus ramas.
Requisitos:
* Git instalado.
* Disponde de un pc Mac, Windows o Linux.

### Comandos de las ramas Master y Develop

Gitflow puede instalarse en cualquier equipo Windows, Linux o macOS de la siguiente forma:
* macOS
Git instalado y funcional: ```$git```
Instalación con Homebrew: ```$ brew install git-flow-avh```
Instalación con Macports: ```$ port install git-flow-avh```
Instalación correcta: ```$ git flow / $ git flow version```
* Linux
Git instalado y funcional: ```$git```
Instalación de la extensión en Debian / Ubuntu: ```$ apt-get install git-flow```
Instalación de la extensión en CentOS / RedHat / Fedora: ```$ sudo dnf install gitflow```
Instalación correcta: ```$ git flow / $ git flow version```
* Windows
Git instalado y funcional: ```$git```
Git for Windows incluye GitFlow por defecto
Instalación correcta: ```$ git flow / $ git flow version```

Para iniciar un repositorio desde cero solo es necesario escribir los siguientes comandos:
```
$ mkdir gitflow-Project
$ git flow init
$ git branch
```

Esto generará un repositorio inicial basado en gitflow y con las ramas principales ya creadas.

### Comandos de la rama Feature

Comandos disponibles a nivel de feature ```$ git flow feature help```
Visualizar lista de ramas de tipo feature ```$ git flow feature list```
Inicia una nueva rama de tipo feature a partir de develop ```$ git flow feature start <nombre>```
Publica rama en el repositorio remoto (Pair Programming) ```$ git flow feature publish <nombre>```
Descarga una rama del repositorio remoto (Pair Programming) ```$ git flow feature track <nombre>```
Descarga el contenido de una feature del repositorio remoto ```$ git flow feature pull origin <nombre>```
Finaliza una rama feature, mergeando con develop ```$ git flow feature finish <nombre>```
Elimina la rama del repositorio local ```$ git flow feature delete <nombre>```

### Comandos de la rama Release

Comandos disponibles a nivel de release ```$ git flow release help```
Visualizar lista de ramas de tipo release ```$ git flow release list```
Inicia una nueva rama de tipo release a partir de develop ```$ git flow release start <versión>```
Publica rama en el repositorio remoto (Pair Programming) ```$ git flow release publish <versión>```
Descarga una rama del repositorio remoto (Pair Programming) ```$ git flow release track <versión>```
Finaliza una rama release, mergeando con develop y master ```$ git flow release finish <versión>```
Elimina la rama del repositorio local ```$ git flow release delete <versión>```

### Comandos de la rama Hotfix

Comandos disponibles a nivel de hotfix  ```$ git flow hotfix help```
Visualizar lista de ramas de tipo hotfix  ```$ git flow hotfix list```
Inicia una nueva rama de tipo hotfix a partir de master  ```$ git flow hotfix start <versión>```
Publica rama en el repositorio remoto (Pair Programming)  ```$ git flow hotfix publish <versión>```
Finaliza una rama hotfix, mergeando con develop y master  ```$ git flow hotfix finish <versión>```
Elimina la rama del repositorio local  ```$ git flow hotfix delete <versión>```

### Merges

Usaremos --no-ff para que el historial no se haga plano.
De esta forma podremos encontrar todos los commits de las ramas.