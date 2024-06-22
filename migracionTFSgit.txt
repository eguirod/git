# ESCENARIO

* El equipo de desarrollo viene de Version Contro(TFS).
* Se requiere la migración a GIT.
* Necesitamos mantener la historia.

# HERRAMIENTA

Git TFS.

Se encuentra alojada en [GitHub] (htts://github.com/git-tfs/git-tfs).
Es completamente opensource y viene muy bien documentado.
La única pega es que ya no está mantenido.

# PASOS PARA LA MIGRACIÓN

## Preparar la migración

* Revisar la estructura del repositorio:
	* Ramas no requeridas.
	* ¿Necesitamos toda la historia?
* Identicamos las ramas:
	* Main
	* Dev
	* Versiones
* Sanear:
	* Limpiamos shelves.
	* Comiteamos todo el código.

## Clone

```
git tfs clone http://tfs:8080/tfs/DefaultCollection$Project1 -from={0} -branches==all
```

* http://tfs:8080/tfs/DefaultCollection$Project1: ruta del tfs
* -from={0}: indicamos desde qué commit queremos clonar (desde le inicio en este caso con 0)
* -branches==all: para indicar las ramas

### Consejos

* Realizarlo desde la máquina dónde esté alojado el TFS.
* Realizar la migración cuando no se esté trabajando.
* --debug para recibir un log más definicio si algo falla

# COMPLICACIONES

## TF40030

El almacén de datos local se está usando actualmente en otra operación.
Se debe a que en la versión de 2015 se pueden localizar en Local y en Servidor.

La solución está en el [repo](https://github.com/jmmortega/git-tfs/tree/bug/TF40030_Error) de José Manuel Montero.
Podemos bajar la rama compilarla en la herramienta y usarla.

## Identificación de changeset.

En caso de la herramienta no encuentre el changeset porque hubiera cosas rarunas en la rama, el proceso se pararía pidiéndonos el changeset.

## No se descargan todas las ramas.

Por la razón que sea se pierde alguna rama.
La mejor forma de recuperarlo es ir rama a rama.
Creamos un nuevo repositorio y clonamos esa rama en ese repositorio.
Ahora en git 