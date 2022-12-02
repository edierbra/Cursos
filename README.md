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

Se seleciona la opcion que aparece en la parte superior en GitHub, de esta manera clona ese repositorio en mi repositorio remoto. Si se quiere tener esto en mi co`mputadora se hace un `git clone`

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

## README.md

Practica muy importante para mostrar o describir lo que se tiene en nuestro repositorio GitHub, el contenido de este archivo se visualiza automaticamente, por lo cual podemos tener lo que sea aqui y poder explicar nuestro repositorio.