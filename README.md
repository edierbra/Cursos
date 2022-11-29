# Curso Profesional de Git y GitHub
**By:** *Edier Dario Bravo Bravo*

# INTRODUCCION A GIT:

![](https://github.com/edierbra/Cursos/blob/main/images/GitHub/intro1.png?raw=true)
![](https://github.com/edierbra/Cursos/blob/main/images/GitHub/intro2.png?raw=true)

## Comandos mas frecuentes

```git init``` Empieza un repositorio en la carpeta actual creando un area en memoria ramm llamanda **staging** o carpeta **.git**.

```git add archivoPlano.txt``` Añade y arranca el archivo **archivoPlano.txt** al area de preparacion (**staging**).

```git commit -m “version 1”``` Crea una instancia del area de preparacion y envía los cambios al sistema de control de versiones.

```git status``` Estado de la base de datos.

```git show``` Muestra los cambios históricos hechos, quien los hizo  y las diferencias respecto a la version mas nueva.

```git log archivoPlano.txt``` Muestra historia completa de un archivo

`git checkout` Trae versiones de otras ramas

## Introducción a la terminal y línea de comandos

`pwd` Muestra directorio donde estoy.

`ls` Lista archivos.

`ls -al` Listar todos los archivos.

`ls -l` Lista archivos menos los ocultos.

`ls -a` Muestra todos los archivos sin detalles.

`git rm archivo.txt` Elimina el archivo del add.

`git rm –cached archivo.txt` Elimina el archivo del add de la ram.

# COMANDOS BASICOS DE GIT

## siempre que se haga un cambio en nuestro repositorio local:

`git add .` o `git add archivo.txt`

`git commit -m “mensaje”`

`git push origin nombreRama`

`git log historia.txt` Muestra los commits, el HEAD indica la versión más reciente.

![](https://github.com/edierbra/Cursos/blob/main/images/GitHub/head.png?raw=true)

## Reset y checkout

`git log` muestra los commit

`git reset codigoCommit --hard` Volver a la version del codigo que indica, todo vuelve a lo anterior y se elimina el historial

`git reset codigoCommit --soft` Volver a la version del codigo que indica, vuelve a la version anterior pero lo del staging no se modifica

`git diff` Muestra diferencia entre lo que tengo en el disco y el commit

`git log --stat` Ver los cambios realizados en cada commit

`git checkout codigoCommit historia.txt` Trae el archivo de esa version del commit

`git checkout nombreRama historia.txt` trae la ultima version de la rama del respectivo archivo

# FLUJO DE TRABAJO BASICO

## Flujo de trabajo básico con un repositorio remoto

`git clone url` clona el master del repositorio Remoto al directorio de trabajo y crea la base de datos con todo el historial de cambios al repositorio local

`git add`, `git commit` y `git push` para mandar cambio al repositorio remoto

`git fetch` solo clona lo de nuestro repositorio remoto al repositorio local. Si se quiere copear a mis archivos se necesita fusionar lo del local y directorio con `git merge`

`git pull` copea todo lo de nuestro repositoria al repositorio local, copea la base de datos y copea en el directorio. (`git fetch` + `git merge`)

## Introducción a las ramas o branches de Git

`git branch nombreRama` crear una nueva rama

`git checkout nombreRama` cambiar a una respectiva rama

El HEAD indica en que version estoy ubicado

`git commit -am "mensage"` = `git add` + `git commit -m "mensage"` solo para casos donde no se crean nuevos archivos

## Fusión de ramas con Git merge

- Importante hacer `git commit` + `git add` en las cabeceras involucradas

- Ubicarse en la rama principal ()

`git merge nombreRamaQuieroUnir` para unir otra rama a la principal

## Resolucion de conflictos al hacer un merge

Los conflictos suceden cuando dos usuarios editan una misma linea de codigo

Se identifica los conflictos en el codigo que aparecen de la siguiente manera y defino con que version quedarme.

```
>>>>>>>>>>>>>HEAD (Current change)
    ...
    codigo
    ...
-----------------
    ...
    codigo
    ...
>>>>>>>>>>>>> (incoming change)
```

# TRABAJANDO CON REPOSITORIOS REMOTOS EN GIT

