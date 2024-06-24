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

