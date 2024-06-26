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

<img width="666" alt="master" src="https://github.com/eguirod/git/assets/71733548/6c85cecb-c61e-4a00-af5c-e8e319d135f7">

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

<img width="693" alt="develop" src="https://github.com/eguirod/git/assets/71733548/eb749aee-6033-49ec-afd9-501aaba8624d">

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
 
<img width="685" alt="feature1" src="https://github.com/eguirod/git/assets/71733548/e772a001-ad6c-4a9c-bbb9-d2da353844e5">
<img width="626" alt="feature2" src="https://github.com/eguirod/git/assets/71733548/321e60e4-c3a5-4202-b3db-7916f964a38e">

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
 
<img width="683" alt="release" src="https://github.com/eguirod/git/assets/71733548/6622bae0-212a-4bcc-a04f-4f5fd7e99793">

### Hotfix

Estas ramas se generan habitualmente cuando se detecta un defecto en producción que debe ser
 corregido con agilidad. Para ello se genera una rama de tipo hotfix, que parte del código
 existente en master.  
Sobre ella pueden realizarse las correcciones que sean necesarias para arreglar el bug, para
 luego volver a mergear con master, añadiéndole un nuevo tag de versión.  
También es necesario mergear con develop para que el defecto también quede corregido en
 desarrollo y si hubiera una release preparada, también se vuelva en la release en cuestión.
 
 <img width="680" alt="hotfix" src="https://github.com/eguirod/git/assets/71733548/ec0ebcd6-69f6-4228-8f2b-adcb39a38f82">

### Uniéndolo todo

Uniéndolo todo, el proceso cobra sentido, y todos los tipos de ramas se complementan los unos
 a los otros para alcanzar los objetivos que propone GitFlow.

<img width="455" alt="todoUnido" src="https://github.com/eguirod/git/assets/71733548/c28c1aeb-7182-4212-ab3a-eb5fcf733cb2">

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

<img width="404" alt="gitFlowRamas" src="https://github.com/eguirod/git/assets/71733548/4ca2240d-c4c3-4097-a4e7-e56cba698f12">

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

<img width="586" alt="mergeNoFF" src="https://github.com/eguirod/git/assets/71733548/41689376-1557-4b8d-af1b-ba1f41946102">

## Revisiones cruzadas

### ¿Qué son las revisiones cruzadas?

La **revisión por pares**(o **Pair Review**) es la revisión de tu código fuente por el resto de
 miembros de tu equipo con el objetivo de encontrar defectos en fases tempranas (fases de
 commit incluso antes de mergear en otras ramas) y proponer mejoras, además de controlar la
 aplicación de reglas de codificación.  
Esta práctica, cuando ya llega a un estado de madurez óptimo, supone un importante ahorro de
 costes derivados en defectos futuros, mejora el feedback en el producto, reduce la
 frustración del equipo y ayuda a mantener unos estándares y reglas de codificación vivos.  
Parte de:
* Compañeros de trabajo y miembros del equipo.
* Todo aquel que tenga interés en el producto en revisión.
* Todo aquel que esté implicado en la calidad de los desarrollos.
Beneficios:
* Ayuda a generar productos comlejos y correctos.
* Establede estándares de referencia para el equipo y promueve su seguimiento.
* Da pie a diferentes puntos de vista.
* Genera métricas para mejorar el proceso y la calidad de los productos.
Cuidado con:
* Puede generar conflictos por disparidad en los criterios de revisión.
* La figura de un líder puede hacer que el resto de los revisores pierdan efectividad.
* Deben ser atómicas, no deben incluir muchos cambios. Mejor fraccionar.
Desventajas:
* Aumenta el Time-to-Market.
* Aumenta el Coste de Desarrollo.
* Aumenta Coste en Herramientas.

### Proceso

Cuando un desarrollador se encuentra próximo a mergear su código con otra rama, genera una
 “Pull Request” o petición de revisión, por la cual otros miembros del equipo dan su
 aprobación o rechazo al cambio introducido.  
Una vez que se cumpla la regla de revisión establecida por el equipo en consenso, se puede
 hacer el merge. Estas reglas pueden ser del tipo, revisar por un número de miembros, un
 senior tiene que dar aceptación… y son establecidas por el propio equipo.

<img width="504" alt="proceso" src="https://github.com/eguirod/git/assets/71733548/5b29db9b-2c5b-48d8-9d0e-0fa36d40646c">


### Establece tus reglas

Cada equipo/proyecto dependiendo de contexto, cliente, filosfía, cultura... determina una serie
 de reglas, por ejemplo:
* Debe haber como mínimo un Junior y un Senior y éste último debe esperar a que el Junior dé su opinión.
* Una pull debe revisarse como máximo 2 días después de su creación.
* Para rechazar es necesario justificar y proponer solución.
* Con tres aprobaciones, se puede mergear.
* El creador de la pull debe perseguir a los revisores.
* No puedes tener más de 3 pull pendientes.
* Cuando "El Experto" apruebe, se puede mergear al margen de las aprobaciones necesarias.

### Herramientas

En el mercado encontramos varias herramientas de gestión de la configuración que ya tienen
 implantado este ciclo de forma opcional en sus procesos, como GitHub, GitLab o Bitbucket,
 pudiendo utilizar la revisión “Pull Request” si el equipo lo determina.
