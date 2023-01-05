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

## Siempre que se haga un cambio en nuestro repositorio local:

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

Los conflictos suceden cuando dos usuarios editan una misma linea de codigo e intentamos fusionar dos ramas con `git merge nombreRamaQuieroUnir`

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

usar: `git log` o `git status` pra ver informacion detallada de los conflictos y asi solucionarlos.

# TRABAJANDO CON REPOSITORIOS REMOTOS EN GIT

## Uso de GitHub

`git remote add origin <url HTTP>` Añadir un repositorio remoto.

`git remote rm origin` elimina repositorio remoto origin (rm = remote).

`git remote set-url origin <url Repositorio Remoto>` Cambiar la url de origin. Aunque siempre va a estar actualizado se recomienda ejecutar `git pull origin nombreRamaRemota`

`git remote` Muestra repositorio remoto.

`git remote -v` mostrar repositorio remoto verbalmente.

`git push origin nombreRamaLocal` Sube al repositorio lo que tenemos localmente en la rama nombreRamaLocal.

O use `git push --set-upstream origin master` si es tu primera vez.

- El anterio codigo aveces coloca problema por que en el repositorio remoto tenemos cosas que localmente no se tienen.

- Se realiza `git pull origin nombreRamaRemoto` para traer todo lo de nuestro repositorio remoto a nuestro repositorio local.

    - Se realiza (Solo si hay problema con el anterior comando)`git pull origin nombreRamaRemoto --allow-unrelated-histories` para forzar a unir reporistorio remoto con el local.

Nuevamente para tener lo mismo remotamente y localmente `git push origin nombreRamaLocal` y se sube al repositorio lo que tenemos localmente en la rama nombreRamaLocal.

al hacer modificaciones directamente en el repositorio remoto, se recomienda hacer `git pull` localmente.

## LLaves publicas y privadas

Lo que se cifra con la llave publica se decifra con la privada, las dos estan vinculadas.

## Configurar llaves SSH en local

`git config -l` ver configuracion de mi git.

**Configuracion de usurio GitHub**

`git config --global user.name "MyUsername"` Agregar usuario GitHub

`git config --global user.email "Tu@correo.com"` Agregar correo gitHub

**Windows** (Importente estar en el Home)

- `ssh-keygen -t rsa -b 4096 -C "tucorreo@domain.com"`, luego te pedira la direccion donde guardar la llave y otras opciones, si le das **ENTER** deja la configuracion por defecto. Este comando crea una carpeta nueva en el directorio del usuario, llamada .ssh, dentro de ella vas a ver la lave publica y la privada.
    - El -t rsa genera una clave con encriptacion RSA.
    - El -b es el tamaño, en este caso es de 4096 bit.
    - El -C le colocas una nota para identificar la llave muy util.
- ingresas la clave rsa, si das **ENTER** la deja vacia.
- `eval $(ssh-agent -s)`, preparar tu agente con tu nueva llave. Esto creara al agente y te dara el numero de pid que esta corriendo.
- `ssh-add ~/.ssh/id_rsa`, Esto creara al agente y te dara el numero de **pid** que esta corriendo
- Te debe salir algo como esto: `/c/User/momoko/.ssh/id_rsa(tucorreo@domain.com)`

**Linux** (Importente estar en el Home)

- `ssh-keygen -t rsa -b 4096 -C "tucorreo@domain.com"`, luego te pedira la direccion donde guardar la llave y otras opciones, si le das **ENTER** deja la configuracion por defecto. Este comando crea una carpeta nueva en el directorio del usuario, llamada .ssh, dentro de ella vas a ver la lave publica y la privada.
- `eval $(ssh-agent -s)`, Crear Agente a usar Llave ssh.
- `ssh-add ~/.ssh/id_rsa`, Agregar Llave ssh al agente para ser usada.
- Te debe salir algo como esto: `/c/User/momoko/.ssh/id_rsa(tucorreo@domain.com)`

**Ahora vamos con GitHub**

- Para añadir una llave SSH a tu cuenta GitHub, ve a la configuracion (Settings) de tu cuenta y selecciona la opcion "llaves SSH y GPG" en el menu de la izquierda.
- En la derecha, haz clic en el boton "Nueva clave de SSH" para crear una nueva clave de SSH para Github.
- El siguiente paso es agregar la contenido dentro de nuestro archivo id_rsa.pub.
- En linux para ver la clave publica se usa `cat ~/.ssh/id_rsa.pub`
- El contenido de la llave publica se ve algo asi: `ssh-rsa B3NzaC1yc2EAAAADAQABAAACAQC+HvRnxwPJyUiUO/UCPKrW6mFPgJF8LxsC2lbBePtn+UDv4Xy+eMJRgG5fbaqy2i0tvPWtO9AAIlclkIVeu5LmV7RaE8H78VXxGVQLcWXvlS0SGlwIxXXd9hBeGh6qPmrya63Ezrt/J1fNy6Ro9s5+ndLogBG2G0JKdAoytbCIBgPmm6sK9nvv3kHrjSK4S0rRz0nb9oaxCQF6V+T75hPgYp+JMOl8yZZMGLN3GPadE2ye2/lskJXzYjlHyjAE6a0g+vrHmMjOULPUrO   tucorreo@domain.com`
- Vas a copiar todo el contenido de la llave y la vas a pegar en github, le das al boton de agregar y listo.
- Recuerda cuando clones tus repositorio tomar la opcion de copiar la url por SSH y no por HTTP.

## Tags y versiones en Git y GitHub

`git log --all --graph` muestra los log pero con graficos

`git log --all --graph --decorate --oneline` muestra los log pero con graficos y resumido

`alias arbolito="<comando>"` asignar alias a una variable

- ejemplo: `alias arbolito="git log --all --graph --decorate --oneline"`

`git tag -a <nombreTag> -m "<Mensaje>" <idCommit>` agregar tag a una respectiva version. **nombreTag** se recomienda segir la estructura: v0.1, v0.2, v0.3, v0.4, ...

`git tag` ver los tag que tenemos

`git show-ref --tags` ver los tag y en donde se encuentran, es decir su referencia.

`git push origin --tags` enviar tags a internet

`git tag - d nombreTag` eliminar un Tag localmente

`git push origin :refs/tags/nombreTag` eliminar tag remoto, importante realizar el anterior comando.

## Manejo de ramas en GitHub

`git checkout nombreRama` para cambiar de rama

`git branch` mostrar las ramas locales

`git branch nombreRamaNueva` crea una rama nueva a partir de donde estoy parado

`git show-branch --all` mostrar ramas detalladamente remotas y locales

`gitk` muestra historia pero graficamente

##  Configurar múltiples colaboradores en un repositorio de GitHub

`git clone <url Repositorio Remoto>` clono un repositorio remoto. De esta manera una persona se uni como colaborador, pero se debe añadir a la persona en los colaboradores del repositorio remoto.

# Flujo de trabajo profecionales

## Flujo de trabajo profesional: Haciendo merge de ramas de desarrollo a master

Se recomienda siempre hacer `git pull` a la rama principal remota antes de iniciar a trabajar e igualmemte antes de ejecutar `git push` para subir al repositorio remoto.

## Utilizando Pull Requests en GitHub

Esto se configura en GitHub en la opcion **Pull Requests** y eligimos la rama base y la que vamos a comparrar, tambien podemos notificar a un colaborador los cambios que se hagan en esta herramienta

Una vez aprovados los cambios ya se puede hacer un merge.

Se recomienda eliminar la rama usada para la pprueba de **pull request**

Se vuelve a la rama principal y se hace `git pull` al reporitorio para actualizar los cambios localmente. 

## Creando un Fork, contribuyendo a un repositorio

Se seleciona la opcion que aparece en la parte superior en GitHub, de esta manera clona ese repositorio en mi repositorio remoto. Si se quiere tener esto en mi computadora se hace un `git clone`

Se puede hacer un pull request desde el proyecto ramificado, de esta manera esperar si el propietario hace los cambios.

Para estar actualizado con el repositorio oficial se crean en consola otro origen con nombre **upstream** y de esta manera hacer `git pull` al master oficial, luego el `git push`a nuestro repositorio remoto al origen `origin`.
Tambien se puede haccer directamente desde GitHuB

## Haciendo deployment a un servidor

Deploy es el proceso que permite enviar al servidor uno o varios archivos. Este servidor puede ser de prueba, desarrollo o produccion.

Pasos para hacer deployment en un servidor web:

- Entrar a la capeta de los archivos del servidor.
- Copiar link en clone, elegir entre HTTPS o SSH del repositorio a contribuir.
    - En la carpeta deseada se clona el repositorio:

    ```
    git clone url
    Deploy:
    ```
- Realizar cambios y commit en GitHub.
- Traer al Repositorio local las actualizacion para el servidor en la capeta de los archivos del servidor.
    ```git pull ramaRemota main```

Siempre se debe proteger el archivo .git. Dependiendo del software para el servidor web, existen diferentes maneras. La conexion entre GitHub y el servidor se puede realizar mediante: Travis (pago) o Jenkis (Open source).

## Ignorar archivos en el repositorio con .gitignore

Se crea unj nuevo archivo **.gitignore** en la cual colocas las extenciones de archivos y carpetas que quieres ignorar para subir al repositorio remoto.

## README

Practica muy importante para mostrar o describir lo que se tiene en nuestro repositorio GitHub, el contenido de este archivo se visualiza automaticamente, por lo cual podemos tener lo que sea aqui y poder explicar nuestro repositorio.

## GitHub Pages

Crear un repositorio con el mismo nombre de mi usuario.

Se crea un archivo index.html, el cual tendra en contenido del inicio de nuestra pagina.

En ajustes de nuestro repositorio configurarr el apartado de **Pages**, dode se elige de que rama cargar el index.html

Entramos nuevamente a ajustes y en este mismo lugar podemos ver el enlace de nuestra pagina.

Si se quiere que la paginma cargue de la raiz modificar el nombre del proyecto a **<nombre_usuario>.github.io**, de esta manera todo quedara listo.

# Multiples entornos de trabajo en Git

## Git Rebase: reorganizando el trabajo realizado

Permite agarrar una rama entera y pegarla a nuestra rama maestra o a cualquiera que deseemos

La rama maestra debe estar mas adelantada, primero hacemos desde nuestra rama secundaria

`git rebase <ramaMaestra>`

Luego desde la rama maestra

`git rebase <ramaSecundaria>`

Y de esta manera se realizan los cambios en nuestra rama maestra.

Podemos hacer **git pull** y **git push** para tener lo mismo remotamente.

## Git Stash: Guardar cambios en memoria y recuperarlos después

El stashed nos sirve para guardar cambios para después, Es una lista de estados que nos guarda algunos cambios que hicimos en Staging para poder cambiar de rama o branch sin perder el trabajo que todavía no guardamos en un commit

Para agregar los cambios al stash se utiliza el comando, el cual guarda los cambios y vuelve al anterior commit realizado

`git stash`

Podemos poner un mensaje en el stash, para asi diferenciarlos en git stash list por si tenemos varios elementos en el stash.

`git stash save "mensaje identificador"`

Ver los Stashed guardados

`git stash list`

Para recuperar los últimos cambios desde el stash a tu staging area

`git stash pop`

Para aplicar los cambios de un stash específico y eliminarlo del stash

`git stash pop stash@{<num_stash>}`

Para retomar los cambios de una posición específica del Stash

`git stash apply stash@{<num_stash>}`

Para crear una rama y aplicar el stash más reciente.

`git stash branch <nombre_de_la_rama>`

Para crear una rama y aplicar un stash especifico.

`git stash branch <nombre_de_la_rama> stash@{<num_stash>}`

Para eliminar los cambios más recientes dentro del stash (el elemento 0)

`git stash drop`

Para eliminar un stash especifico

`git stash drop stash@{<num_stash>}`

Para eliminar todos los elementos del stash

`git stash clear`

**Consideraciones:**
- El cambio más reciente (al crear un stash) SIEMPRE recibe el valor 0 y los que estaban antes aumentan su valor.
- Al crear un stash tomará los archivos que han sido modificados y eliminados. Para que tome un archivo creado es necesario agregarlo al Staging Area con git add [nombre_archivo] con la intención de que git tenga un seguimiento de ese archivo, o también utilizando el comando git stash -u (que guardará en el stash los archivos que no estén en el staging).
- Al aplicar un stash este no se elimina, es buena práctica eliminarlo.

## Git Clean: limpiar tu proyecto de archivos no deseados

Mientras estamos trabajando en un repositorio podemos añadir archivos a él, que realmente no forma parte de nuestro directorio de trabajo, archivos que no se deberían de agregar al repositorio remoto.

El comando **clean** actúa en archivos sin seguimiento, este tipo de archivos son aquellos que se encuentran en el directorio de trabajo, pero que aún no se han añadido al índice de seguimiento de repositorio con el comando **add**.

Revidsar que archivos no tienen seguimiento (simula que se va a eliminar)

`git clean --dry-run`

Eliminar los archivos listados de no seguimiento

`git clean -f`

Git clean solo borra archivos no carpetas, ademas los archivos en **.gitignore** no se eliminaran

Ver todos los comandos de git clean en la [documentacion oficial](https://git-scm.com/docs/git-clean)

## Git cherry-pick: traer commits viejos al head de un branch

Git Cherry-pick es un comando que permite tomar uno o varios commits de otra rama o branch sin tener que hacer un merge completo. Así, gracias a cherry-pick, podríamos aplicar los commits relacionados con nuestra funcionalidad en la rama master sin necesidad de hacer un merge.

Se usa el siguiente comandondesde la rama donde quiero hacer el cambio

`git cherry-pick <codigo_commit>`

# Comandos de Git para casos de emergencia

## Git Reset y Reflog: úsese en caso de emergencia

Para ver todo el historial aunque ya no aparezcan en los log se usa

`git reflog`

Para volover al estado donde todo funcionaba corretamente

`git reset  HEAD@{<head_num>}`

- `git reset --soft <codigoHashDelHEAD>` te mantiene lo que tengas en staging ahí.
- `git reset --hard <codigoHashDelHEAD>` resetea absolutamente todo incluyendo lo que tengas en staging.

## Reconstruir commits en Git con amend

Este comando sirve para agregar archivos nuevos o actualizar el commit anterior y no generar commits innecesarios. También es una forma sencilla de editar o agregar comentarios al commit anterior porque abrirá la consola para editar este commit anterior.

luego de hacer los cambios se ejecuta

```
git add <archivosModivicados>
git commit --amend
```

Al abrirse la consola para editar este commit anterior y una vez editado se pulza la tecla **ESC** y luego **SHIFT + Z + Z**

## Buscar en archivos y commits de Git con Grep y log

Busca en todo el proyecto los archivos en donde está una cierta palabra

`git grep <palabra>`

Buscar en que linea esta una cierta palabra.

`git grep -n <palabra>` 

Buscar en que archivo y cuantas veces se repite en este cierta palabra. si la palbra es un atributo colocarlo entre comillas (**"\<p>"**)

`git grep -c <palabra>`

Para buscar una palabra entre los commits

`git log -S "<palabra>"`

# Bonus sobre Git y Github

## Comandos y recursos colaborativos en Git y GitHub

A continuación veremos una lista de comandos colaborativos para facilitar el trabajo remoto en GitHub:

- `git shortlog` permite ver en formato log los commit de cada mienbro del eqipo
- `git shortlog -sn` muestra cuantos commit han hecho cada miembro del equipo.
- `git shortlog -sn --all` muestra cuantos commit han hecho cada miembro del equipo, hasta los que han sido eliminados.
- `git shortlog -sn --all --no-merge` muestra cuantos commit ha hecho cada miembro, quitando los eliminados sin los merges.
- `git config --global alias.<nombreComando> "<comando>"` para guardar un comando en la configuracion global y luego ejecutarlo.
**Ejemplo:** `git config --global alias.stats "shortlog -sn --all --no-merges"`
**ejecucion:** `git stats`
- `git blame <ARCHIVO>` muestra quien hizo cada cosa línea por línea. Si se coloca la bandera **-c** permite identar mejor el resulado a mostrar
- `git COMANDO --help` muestra como funciona el comando.
- `git blame <ARCHIVO> -L<linea_inicial>,<Linea_final>` muestra quien hizo cada cosa línea por línea, indicándole desde qué línea ver. **Ejemplo:** -L35,50.
- `git branch -r` se muestran todas las ramas remotas.
- `git branch -a` se muestran todas las ramas, tanto locales como remotas.
- En la opcion **insights** en nuestra cuenta de GitHub podemos ver mas estadisticas sobre los integrantes que han aportado al proyecto

# RESPUESTAS

![](https://github.com/edierbra/Cursos/blob/main/images/GitHub/respuestas.png?raw=true)
