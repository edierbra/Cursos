# Git y Github Course
**By:** *Edier Dario Bravo Bravo*

# Introduction:

![](https://github.com/edierbra/Cursos/blob/main/images/GitHub/intro1.png?raw=true)
![](https://github.com/edierbra/Cursos/blob/main/images/GitHub/intro2.png?raw=true)

## Comandos mas frecuentes

```git init``` Empieza un repositorio en la carpeta actual.
```git add archivoPlano.txt``` Añade y arranca el archivo **archivoPlano.txt** al area de preparacion.
```git commit -m “version 1”``` Crea una instancia del area de preparacion y envía los cambios al sistema de control de versiones.
```git status``` Estado de la base de datos.
```git show``` Muestra los cambios históricos hechos y quien los hizo.
```git log archivoPlano.txt``` Muestra historia completa de un archivo

## Introducción a la terminal y línea de comandos
`pwd` Muestra directorio donde estoy
`ls` Lista archivos
`ls -al` Listar todos los archivos
`ls -l` Lista archivos menos los ocultos
`ls -a` Muestra todos los archivos sin detalles
`git rm archivo.txt` Elimina el archivo del add
`git rm –cached archivo.txt` Elimina el archivo del add de la ram

##### siempre que se haga un cambio en nuestro repositorio local:
`git add .` o `git add archivo.txt`
`git commit -m “mensaje”`
`git log historia.txt` Muestra los commits, el HEAD indica la versión más reciente.
![](https://github.com/edierbra/Cursos/blob/main/images/GitHub/head.png?raw=true)

