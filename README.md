                        ██████╗ ██╗████████╗       ██╗   
                       ██╔════╝ ██║╚══██╔══╝       ██║   
                       ██║  ███╗██║   ██║       ████████╗
                       ██║   ██║██║   ██║       ██╔═██╔═╝
                       ╚██████╔╝██║   ██║       ██████║  
                        ╚═════╝ ╚═╝   ╚═╝       ╚═════╝  
                                                         
                  ██████╗ ██╗████████╗██╗  ██╗██╗   ██╗██████╗ 
                 ██╔════╝ ██║╚══██╔══╝██║  ██║██║   ██║██╔══██╗
                 ██║  ███╗██║   ██║   ███████║██║   ██║██████╔╝
                 ██║   ██║██║   ██║   ██╔══██║██║   ██║██╔══██╗
                 ╚██████╔╝██║   ██║   ██║  ██║╚██████╔╝██████╔╝
                  ╚═════╝ ╚═╝   ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚═════╝ 

# Qué es Git y GitHub

Git es un software de control de versiones diseñado por Linus Torvalds, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente.

En su lugar GitHub es una forma para alojar proyectos utilizando el sistema de control de versiones Git. GitHub sería la red social de código para los programadores, tu propio curriculum vitae.

# Instalación Git en Linux

Para actualizar a la ultima version utilizamos lo siguiente desde nuestra terminal

```sh
# Actualizar git a la ultima version
$ sudo add-apt-repository ppa:git-core/ppa 
$ sudo apt-get update 
$ sudo apt-get upgrade
$ sudo apt-get install git
```

# Creando repositorio de Git y primer commit

Cuando inicias Git en la carpeta o en la carpeta que le indiques creara un archivo .git el cual contendrá toda la información necesaria para seguir los cambios realizados.

Iniciar Git

- `git init` -> Inicia Git dentro de la carpeta en la que nos encontremos
- `git init <carpeta>` -> Inicia Git dentro de la carpeta especificada
- `git init <newFolder>` -> Inicia Git dentro de la carpeta a crear

Añadir archivo al **staged** (memoria ram y esta siendo tracked o revisando si hay cambios) para después hacer un commit

- `git add <fileName>` -> Agregar al staged el archivo seleccionado
- `git add $PATH <./>` -> Agregar con la ruta definida
- `git add all` -> Añadir todos los archivos al staged

**Commit** es la forma en la que ya se envían los cambios al repositorio después de ser traqueados, esto indica que sera guardado ese ultimo staged.

- `git commit -m "Mensaje del commit"` -> Enviar los cambios rastreados al repositorio
- `git commit -am "Mensaje del commit"` -> Agregar y mensaje

# Configurando nuestro Git

Para hacer un commit Git nos pide identificarnos, en otras palabras ¿quine esta haciendo este commit? En principio nos triará las varias de entorno de nuestro computador en el caso de Mac traerá la cuenta del apple id, para configurar hacemos lo siguiente:

- `git config` -> mostrara lo que puedes hacer con las configurations
- `git config --list` -> Mostrará la lista de configuraciones
- `git config --global` -> Insertara la configuración que le pasemos en el archivo .gitconfig
- `git config --list --show-origin` -> Mostrar ruta de las configuraciones
- `git config --global user.email "tu@correo.com"`
- `git config --global user.name "tuNombre"`
- `git config --global init.defaultbranch main` -> Cambiar master por main

Para ver el historial de cambios o commits realizados

- `git log` -> Mostrar el historial de todos los archivos
- `git log <fileName>` -> Mostrara el historial de commits del archivo específicos.

# Analizando cambios en los archivos

- `git show` -> Muestra el último commit realizado y sus cambios con respecto al anterior commit en todo el proyecto.
- `git show <fileName>` -> Muestra el ultimo commit realizado y sus cambios con respecto al anterior commit en el archivo especificado.
- `git diff commitA commitB` -> Muestra las diferencias entre los diferentes commits o el
  proyecto.

# ¿Qué es un Branch (rama) y cómo funciona un Merge en Git?

Las ramos o branch nos ayudan a tener un flujo de trabajo de nuestro proyecto, donde la rama principal (main) es lo que va producción y las demás ramas son organización para el equipo como la rama develop, feature, release, hotfix, los cuales son solo nombres propuestos por los expertos para llevar acabo el desarrollo de un proyecto se pueden cambiar.

Esas ramas serán después fusionadas con la rama principal (main) y así seguir un flujo de trabajo.

> Crear una nueva rama lo conocemos como branch. Unir dos ramas lo conocemos como Merge.

# ¿Qué es el staging y los repositorios? Ciclo básico de trabajo en Git

Para iniciar un repositorio, o sea, activar el sistema de control de versiones de Git en tu proyecto, solo debes ejecutar el comando `git init`.

Este comando se encargará de dos cosas: primero, crear una carpeta .git, donde se guardará toda la base de datos con cambios atómicos de nuestro proyecto; y segundo, crear un área que conocemos como Staging, que guardará temporalmente nuestros archivos (cuando ejecutemos un comando especial para eso) y nos permitirá, más adelante, guardar estos cambios en el repositorio (también con un comando especial).

Ciclo de vida o estados de los archivos en Git:

Cuando trabajamos con Git nuestros archivos pueden vivir y moverse entre 4 diferentes estados (cuando trabajamos con repositorios remotos pueden ser más estados, pero lo estudiaremos más adelante):

- **Archivos Tracked**: son los archivos que viven dentro de Git, no tienen cambios pendientes y sus últimas actualizaciones han sido guardadas en el repositorio gracias a los comandos git add y git commit.
- **Archivos Staged**: son archivos en Staging. Viven dentro de Git y hay registro de ellos porque han sido afectados por el comando git add, aunque no sus últimos cambios. Git ya sabe de la existencia de estos últimos cambios, pero todavía no han sido guardados definitivamente en el repositorio porque falta ejecutar el comando git commit.
- **Archivos Unstaged**: entiéndelos como archivos “Tracked pero Unstaged”. Son archivos que viven dentro de Git pero no han sido afectados por el comando git add ni mucho menos por git commit. Git tiene un registro de estos archivos, pero está desactualizado, sus últimas versiones solo están guardadas en el disco duro.
- **Archivos Untracked**: son archivos que NO viven dentro de Git, solo en el disco duro. Nunca han sido afectados por git add, así que Git no tiene registros de su existencia.
Recuerda que hay un caso muy raro donde los archivos tienen dos estados al mismo tiempo: staged y untracked.
Esto pasa cuando guardas los cambios de un archivo en el área de Staging (con el comando git add), pero antes de hacer commit para guardar los cambios en el repositorio haces nuevos cambios que todavía no han sido guardados en el área de Staging (en realidad, todo sigue funcionando igual pero es un poco divertido).
Comandos para mover archivos entre los estados de Git:

- `git status`: nos permite ver el estado de todos nuestros archivos y carpetas.
- `git add`: nos ayuda a mover archivos del Untracked o Unstaged al estado Staged. Podemos usar git nombre-del-archivo-o-carpeta para añadir archivos y carpetas individuales o git add -A para mover todos los archivos de nuestro proyecto (tanto Untracked como Unstaged).
- `git reset HEAD`: nos ayuda a sacar archivos del estado Staged para devolverlos a su estado anterior. Si los archivos venían de Unstaged, vuelven allí. Y lo mismo se venían de Untracked.
- `git commit`: nos ayuda a mover archivos de Unstaged a Tracked. Esta es una ocasión especial, los archivos han sido guardados o actualizados en el repositorio. Git nos pedirá que dejemos un mensaje para recordar los cambios que hicimos y podemos usar el argumento -m para escribirlo (git commit -m "mensaje").
- `git rm`: este comando necesita alguno de los siguientes argumentos para poder ejecutarse correctamente:
- `git rm --cached`: Mueve los archivos que le indiquemos al estado Untracked.
- `git rm --force`: Elimina los archivos de Git y del disco duro. Git guarda el registro de la existencia de los archivos, por lo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).

![Imagen-Freddy](https://static.platzi.com/media/public/uploads/capture1_44e940e0-77b2-4f04-b76d-d7637b4ca7a7.PNG)

# Volviendo en el tiempo en nuestro repositorio utilizando reset y CHECKOUT

Checkout esto seria un cambio que no afecte

- `git checkout + idCommit + fileName`-> Volver a la version especificada de un archivo o proyecto

Git rm

- `git rm --cached` -> Elimina los archivos de nuestro repositorio local y del área de staging, pero los mantiene en disco duro o local.
- `git rm --force` -> Elimina los archivos de Git y del disco duro.

*Reset* borra todo el historial

- `git reset --soft` -> Borramos todo el historial y los registros de Git pero guardamos los cambios que tengamos en Staging

# Flujo de trabajo básico con un repositorio remoto

Un servidor remoto es donde se concentra todos los commits y archivos de texto plano para trabajar remotamente con equipo de trabajo o personales, estos servidores pueden ser como GitHub, GitLab, etc...

Con esto explicamos un poco el flujo de trabajo

  > Directorio -> Staging -> Repositorio Local -> Repositorio Remoto

- `git clone url_del_servidor_remoto` -> Nos permite descargar los archivos de la última versión de la rama principal y todo el historial de cambios en la carpeta .git.
- `git push` -> Luego de hacer git add y git commit debemos ejecutar este comando para mandar los cambios al servidor remoto.
- `git fetch` -> Lo usamos para traer actualizaciones del servidor remoto y guardarlas en nuestro repositorio local (en caso de que hayan, por supuesto).
- `git merge` -> También usamos el comando git merge con servidores remotos. Lo necesitamos para combinar los últimos cambios del servidor remoto y nuestro directorio de trabajo.
- `git pull` -> Básicamente, git fetch y git merge al mismo tiempo.

# El flujo general de GIT-FLOW es

- Se develop crea una rama a partir de main
- Se release crea una rama a partir de develop
- Feature las ramas se crean a partir de develop
- Cuando feature se completa, se fusiona con la develop rama.
- Cuando la release rama está terminada, se fusiona en develop y main
- Si main se detecta un problema en, hotfix se crea una rama desde main
- Una vez que hotfix se completa, se fusiona con ambos develop y main
- [Gitflow-cheatsheet](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
- [Gitflow-tutoriales](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

![Imagen-Fredy](https://static.platzi.com/media/public/uploads/branches_f9d7e237-6a15-4143-a4e9-cc5af06be833.PNG)

# Introducción a las ramas o branches de Git

Las ramas o branches en Git son la forma de divider nuestro proyecto y hacer cambios en el sin afectar el flujo de trabajo de la rama principal o de la que sera enviada a producción, son utilizadas para las mejoras actualizaciones o reparación de algún bug. Esto con la intención de que rama principal (main) la cual contiene nuestro primera version de nuestra web se vea afectada.

**¿Cómo crear ramas?** Al momento de crear una rama con el comando en terminal, lo que hace es copiar el proyecto y sus commit desde el origen hasta la nueva rama. Por eso es importante que creemos estas ramas desde la versión de producción y a su vez sigamos creando ramas para sus diferentes aplicaciones, release´s, develop, hotfix, etc... Dependiendo la organización del proyecto.

- `git branch <branchName>` -> Crea una rama y copia los commits
- `git checkout <branchName>` -> Movernos entre ramas
- `git checkout -b <new-branchName>` -> Crear nueva rama y pasarnos a ella
- `git branch -D <branchName>` -> Borrar rama

# Fusión de ramas con Git merge

El comando `git merge <branchName>` crea un nuevo commit con la fusion de ambas ramas (La rama donde nos encontramos cuando ejecutamos el comando y a rama que indicamos después del comando).

Ahora podemos crear más ramas desde el archivo maestro o principal, ya que es el de producción.

# Resolución de conflictos al hacer un merge

Los conflictos son generados al momento que se editan las mismas lineas de código en diferentes ramas y lo que trata de hacer git es comparar esos cambios para que tu puedas solucionar ese conflicto a mano, por decir algo. Al momento de detectar un conflicto te avisara y tendrás varias opciones:

1. Puedes solucionar el conflicto con la ayuda de visual studio y aceptar los cambios que vienen o no.
2. Puedes abortar el merge y solucionar el problema después de abortarlo con tu equipo de trabajo `git merge --abort`.

> NOTA.- Al solucionar los conflictos desde una de las ramas, la otra dejara de tener el conflicto por lo cual al momento de pasar a la otra rama puedes hacer un merge y no saldrá ningún conflicto y pasaran los cambios efectuados sin problema.

# Cambios en GitHub: de master a main

Desde el 1 de octubre de 2020 GitHub cambió el nombre de la rama principal: ya no es “master” -como aprenderás en el curso- sino main.
Este derivado de una profunda reflexión ocasionada por el movimiento #BlackLivesMatter.

```sh
git config --global init.defaultbranch main
```

# Uso de GitHub

Pasos para crear un repositorio en la plataforma de de GitHub.

1. Crear una cuenta si no la tenemos.
2. Crear un nuevo repositorio.
3. Podemos añadir un origen remoto con el comando `git remote add <nameOrigin> <dirección https> o <SSH> del repositorio en GitHub`
4. Revisar si se ha creado el origin correctamente con el comando `git remote -v` que nos mostrara el nombre que le pusimos y url donde esta para hacer fetch o pull.
5. Hacer pull del origin a nuestro local con el comando `git pull <nameOrigin> <localOrigin>` esto traerá un problema que describiré en notas.
6. Hacer un push al origen remoto del origen local `git push <origenRemoto> <origenLocal>` esto subirá el contenido local al servidor de GitHub.

> NOTA.- Generalmente si al crear el repositorio no creas un readme por defecto, no tendrás problema para hacer un pull del remoto, pero si fue asi lo que hiciste en realidad fue crear una historia de contenido no relacionada, lo que ocasionara un problema como el siguiente:

```sh
Desde https://github.com/eduvj91/Hyperblog
 * branch            main       -> FETCH_HEAD
ayuda: Hacer un pull sin especificar cómo reconciliar las ramas es poco
ayuda: recomendable. Puedes eliminar este mensaje usando uno de los
ayuda: siguientes comandos antes de tu siguiente pull:
ayuda: 
ayuda:   git config pull.rebase false  # hacer merge (estrategia por defecto)
ayuda:   git config pull.rebase true   # aplicar rebase
ayuda:   git config pull.ff only       # aplicar solo fast-forward
ayuda: 
ayuda: Puedes reemplazar "git config" con "git config --global" para aplicar
ayuda: la preferencia en todos los repositorios. Puedes también pasar --rebase,
ayuda: --no-rebase, o --ff-only en el comando para sobrescribir la configuración
ayuda: por defecto en cada invocación.
ayuda: 
fatal: rehusando fusionar historias no relacionadas
```

Comenta dos partes la forma en la que quieres que se reconcilien las ramas si con merge, rebase o sin ninguna y la segunda es que se rehusá fusionar las historias que son distintas. La solución:
`git pull origin main --allow-unrelated-histories` -> Forzar la fusion de las historias en una.
Ya puedes hacer push al origin remoto en GitHub.

# Cómo funcionan las llaves públicas y privadas

Las llaves públicas y privadas nos ayudan a cifrar y descifrar nuestros archivos de forma que los podamos compartir sin correr el riesgo de que sean interceptados por personas con malas intenciones.

La forma de hacerlo es la siguiente:

1. Ambas personas deben crear su llave pública y privada.  
2. Ambas personas pueden compartir su llave pública a las otras partes (recuerda que esta llave es pública, no hay problema si la “interceptan”).
3. La persona que quiere compartir un mensaje puede usar la llave pública de la otra persona para cifrar los archivos y asegurarse que solo puedan ser descifrados con la llave privada de la persona con la que queremos compartir el mensaje.
4. El mensaje está cifrado y puede ser enviado a la otra persona sin problemas en caso de que los archivos sean interceptados.
5. La persona a la que enviamos el mensaje cifrado puede usar su llave privada para descifrar el mensaje y ver los archivos.

Puedes compartir tu llave pública pero nunca tu llave privada.

En la siguiente clase vamos a crear nuestras llaves para compartir archivos con GitHub sin correr el riesgo de que sean interceptados.

## Configura tus llaves SSH en local

Primer paso: Generar tus llaves SSH. Recuerda que es muy buena idea proteger tu llave privada con una contraseña.

`ssh-keygen -t rsa -b 4096 -C "tu@email.com"`
Segundo paso: Terminar de configurar nuestro sistema.

En Windows y Linux:

```sh
# Encender el "servidor" de llaves SSH de tu computadora:
eval $(ssh-agent -s)

# Añadir tu llave SSH a este "servidor":
ssh-add ruta-donde-guardaste-tu-llave-privada
```

En Mac:

```sh
# Encender el "servidor" de llaves SSH de tu computadora:
eval "$(ssh-agent -s)"

# Si usas una versión de OSX superior a Mac Sierra (v10.12)
# debes crear o modificar un archivo "config" en la carpeta
# de tu usuario con el siguiente contenido (ten cuidado con
# las mayúsculas):
Host *
        AddKeysToAgent yes
        UseKeychain yes
        IdentityFile ruta-donde-guardaste-tu-llave-privada

# Añadir tu llave SSH al "servidor" de llaves SSH de tu
# computadora (en caso de error puedes ejecutar este
# mismo comando pero sin el argumento -K):
ssh-add -K ruta-donde-guardaste-tu-llave-privada
```

# Conexión a GitHub con SSH

Luego de crear nuestras llaves SSH podemos entregarle la llave pública a GitHub para comunicarnos de forma segura y sin necesidad de escribir nuestro usuario y contraseña todo el tiempo.

Para esto debes entrar a la Configuración de Llaves SSH en GitHub, crear una nueva llave con el nombre que le quieras dar y el contenido de la llave pública de tu computadora.

Ahora podemos actualizar la URL que guardamos en nuestro repositorio remoto, solo que, en vez de guardar la URL con HTTPS, vamos a usar la URL con SSH:

`git remote set-url origin url-ssh-del-repositorio-en-github`

> NOTA.- Es importante hacer pull antes de hacer push por cualquier cambio que se aya hecho al repositorio remoto para no generar ningún conflicto.

# Tags y versiones en Git y GitHub

Los tags o etiquetas nos permiten asignar versiones a los commits con cambios más importantes o significativos de nuestro proyecto.

Comandos para trabajar con etiquetas:

- Crear un nuevo tag y asignarlo a un commit: `git tag -a nombre-del-tag id-del-commit`
- Borrar un tag en el repositorio local: `git tag -d nombre-del-tag`
- Listar los tags de nuestro repositorio local: `git tag o git show-ref --tags`
- Publicar un tag en el repositorio remoto: `git push origin --tags`
- Borrar un tag del repositorio remoto: `git tag -d nombre-del-tag y git push origin :refs/tags/nombre-del-tag`

# Manejo de ramas en GitHub

Puedes trabajar con multiples ramas que puedes o no enviar a GitHub y viceversa ramas que no necesitaras en local.

- Crear una rama: `git branch <branchNeme>`
- Enviar rama al repositorio remoto: `git push <branchName>`
- Ver ramas `git show-branch --all` o `git branch -a`
- Borrar ramas: `git branch -D <branchName>` y después hacer el push al origen remoto

> NOTA.- Recuerda hacer pull del origin y estar actualizado antes de hacer un push.

# Configurar múltiples colaboradores en un repositorio de GitHub

Por defecto, cualquier persona puede clonar o descargar tu proyecto desde GitHub, pero no pueden crear commits, ni ramas, ni nada.

Existen varias formas de solucionar esto para poder aceptar contribuciones. Una de ellas es añadir a cada persona de nuestro equipo como colaborador de nuestro repositorio.

Solo debemos entrar a la configuración de colaboradores de nuestro proyecto (Repositorio > Settings > Collaborators) y añadir el email o username de los nuevos colaboradores.

Lo siguiente sera que el colaborador configurara su entorno de trabajo git e hiciera 2 cosas.

1. Hacer un git clone del repositorio al que se quiere unir
2. Configurar el origen remoto con SHH para que no le pida la contraseña
Listo podrá hacer pull y push del repositorio.

# Flujo de trabajo profesional con Pull requests

En un entorno profesional normalmente se bloquea la rama master, y para enviar código a dicha rama pasa por un code review y luego de su aprobación se unen códigos con los llamados merge request.

Para realizar pruebas enviamos el código a servidores que normalmente los llamamos staging develop (servidores de pruebas) luego de que se realizan las pruebas pertinentes tanto de código como de la aplicación estos pasan a el servidor de producción con el ya antes mencionado merge request.

# Pull Request en GitHub

Pull request:
Es una funcionalidad de github (en gitlab llamada merge request y en bitbucket push request), en la que un colaborador pide que revisen sus cambios antes de hacer merge a una rama, normalmente master.

Al hacer un pull request se genera una conversación que pueden seguir los demás usuarios del repositorio, así como autorizar y rechazar los cambios.

El flujo del pull request es el siguiente

Se trabaja en una rama paralela los cambios que se desean, crear rama: `(git checkout -b <rama>)`
Se hace un commit a la rama `(git commit -am '<Comentario>')`
Se suben al remoto los cambios `(git push origin <rama>)`
En GitHub se hace el pull request comparando la rama master con la rama del fix.
Uno, o varios colaboradores revisan que el código sea correcto y dan feedback (en el chat del pull request)
El colaborador hace los cambios que desea en la rama y lo vuelve a subir al remoto (automáticamente jala la historia de los cambios que se hagan en la rama, en remoto)
Se aceptan los cambios en GitHub
Se hace merge a master desde GitHub

> Importante: Cuando se modifica una rama, también se modifica el pull request.

# Fork o bifurcaciones

Forks o Bifurcaciones
Es una característica única de GitHub en la que se crea una copia exacta del estado actual de un repositorio directamente en GitHub, éste repositorio podrá servir como otro origen y se podrá clonar (como cualquier otro repositorio), en pocas palabras, lo podremos utilizar como un git cualquiera
.
Un fork es como una bifurcación del repositorio completo, tiene una historia en común, pero de repente se bifurca y pueden variar los cambios, ya que ambos proyectos podrán ser modificados en paralelo y para estar al día un colaborador tendrá que estar actualizando su fork con la información del original.
.
Al hacer un fork de un proyecto en GitHub, te conviertes en dueño del repositorio fork, puedes trabajar en éste con todos los permisos, pero es un repositorio completamente diferente que el original, teniendo alguna historia en común.
.
Los forks son importantes porque es la manera en la que funciona el open source, ya que, una persona puede no ser colaborador de un proyecto, pero puede contribuir al mismo, haciendo mejor software que pueda ser utilizado por cualquiera.
.
Al hacer un fork, GitHub sabe que se hizo el fork del proyecto, por lo que se le permite al colaborador hacer pull request desde su repositorio propio.

Trabajando con más de 1 repositorio remoto
Cuando trabajas en un proyecto que existe en diferentes repositorios remotos (normalmente a causa de un fork) es muy probable que desees poder trabajar con ambos repositorios, para ésto puedes crear un remoto adicional desde consola.

`git remote add <nombre_del_remoto> <url_del_remoto>`
`git remote upstream https://github.com/freddier/hyperblog`
Al crear un remoto adicional podremos, hacer pull desde el nuevo origen (en caso de tener permisos podremos hacer fetch y push)

`git pull <remoto> <rama>`
`git pull upstream master`
Éste pull nos traerá los cambios del remoto, por lo que se estará al día en el proyecto, el flujo de trabajo cambia, en adelante se estará trabajando haciendo pull desde el upstream y push al origin para pasar a hacer pull request.

`git pull upstream master`
`git push origin master`

# Ignorar archivos en el repositorio con .gitignore

Por diversas razones, no todos los archivos que agregas a un proyecto deberían guardarse en un repositorio, ésto porque hay archivos que no todo el mundo debería de ver, y hay archivos que al estar en el repositorio alentá el proceso de desarrollo (por ejemplo los binary large objects, blob, que se tardan en descargarse).
.
Para que no se suban estos archivos no deseados se puede crear un archivo con el nombre .gitignore en la raíz del repositorio con las reglas para los archivos que no se deberían subir, ver sintaxis de los .gitignore <https://git-scm.com/docs/gitignore>
.
Las razones principales para tomar la decisión de no agregar un archivo a un repositorio son:

- Es un archivo con contraseñas (normalmente con la extensión .env)
- Es un blob (binary large object, objeto binario grande), mismos que son difíciles de gestionar en git.
- Son archivos que se generan corriendo comandos, por ejemplo la carpeta node_modules que genera npm al correr el comando npm install

Puedes subir imágenes de manera gratuita en la siguiente página: imgur.com

# Tu sitio web público con GitHub Pages

Entrar a GitHub pages y seguir las instrucciones

# Rebase: reorganizar el trabajo realizado

El comando rebase es una mala práctica, nunca se debe usar, pero para efectos del curso te lo vamos a enseñar para que hagas tus propios experimentos. Con rebase puedes recoger todos los cambios confirmados en una rama y ponerlos sobre otra.

Cambiamos a la rama que queremos traer los cambios: `git checkout experiment`
Aplicamos rebase para traer los cambios de la rama que queremos `git rebase master`

En general hay que hacer primero rebase a la rama que se va a borrar y después rebase a la rama en la que se unirán estos commits

# Git Stash: Guardar cambios en memoria y recuperarlos después

**Stashed:**
El stashed nos sirve para guardar cambios para después, Es una lista de estados que nos guarda algunos cambios que hicimos en Staging para poder cambiar de rama sin perder el trabajo que todavía no guardamos en un commit

Ésto es especialmente útil porque hay veces que no se permite cambiar de rama, ésto porque porque tenemos cambios sin guardar, no siempre es un cambio lo suficientemente bueno como para hacer un commit, pero no queremos perder ese código en el que estuvimos trabajando.

El stashed nos permite cambiar de ramas, hacer cambios, trabajar en otras cosas y, más adelante, retomar el trabajo con los archivos que teníamos en Staging pero que podemos recuperar ya que los guardamos en el Stash.

**git stash**
El comando git stash guarda el trabajo actual del Staging en una lista diseñada para ser temporal llamada Stash, para que pueda ser recuperado en el futuro.

Para agregar los cambios al stash se utiliza el comando:

git stash
Podemos poner un mensaje en el stash, para asi diferenciarlos en git stash list por si tenemos varios elementos en el stash. Ésto con:

`git stash save "mensaje identificador del elemento del stashed"`

Obtener elementos del stash
El stashed se comporta como una Stack de datos comportándose de manera tipo LIFO (del inglés Last In, First Out, «último en entrar, primero en salir»), así podemos acceder al método pop.

El método pop recuperará y sacará de la lista el último estado del stashed y lo insertará en el staging area, por lo que es importante saber en qué branch te encuentras para poder recuperarlo, ya que el stash será agnóstico a la rama o estado en el que te encuentres, siempre recuperará los cambios que hiciste en el lugar que lo llamas.

Para recuperar los últimos cambios desde el stash a tu staging area utiliza el comando:
`git stash pop`

Para aplicar los cambios de un stash específico y eliminarlo del stash:
`git stash pop stash@{<num_stash>}`

Para retomar los cambios de una posición específica del Stash puedes utilizar el comando:
`git stash apply stash@{<num_stash>}`
Donde el <num_stash> lo obtienes desde el git stash list

Listado de elementos en el stash
Para ver la lista de cambios guardados en Stash y así poder recuperarlos o hacer algo con ellos podemos utilizar el comando:
`git stash list`

Retomar los cambios de una posición específica del Stash || Aplica los cambios de un stash específico

Crear una rama con el stash
Para crear una rama y aplicar el stash mas reciente podemos utilizar el comando
`git stash branch <nombre_de_la_rama>`

Si deseas crear una rama y aplicar un stash específico (obtenido desde git stash list) puedes utilizar el comando:
`git stash branch nombre_de_rama stash@{<num_stash>}`
Al utilizar estos comandos crearás una rama con el nombre <nombre_de_la_rama>, te pasarás a ella y tendrás el stash especificado en tu staging area.

Eliminar elementos del stash
Para eliminar los cambios más recientes dentro del stash (el elemento 0), podemos utilizar el comando:
`git stash drop`

Pero si en cambio conoces el índice del stash que quieres borrar (mediante git stash list) puedes utilizar el comando:
`git stash drop stash@{<num_stash>}`
Donde el <num_stash> es el índice del cambio guardado.

Si en cambio deseas eliminar todos los elementos del stash, puedes utilizar:
`git stash clear`

Consideraciones:

El cambio más reciente (al crear un stash) SIEMPRE recibe el valor 0 y los que estaban antes aumentan su valor.
Al crear un stash tomará los archivos que han sido modificados y eliminados. Para que tome un archivo creado es necesario agregarlo al Staging Area con git add [nombre_archivo] con la intención de que git tenga un seguimiento de ese archivo, o también utilizando el comando git stash -u (que guardará en el stash los archivos que no estén en el staging).
Al aplicar un stash este no se elimina, es buena práctica eliminarlo.

# Git Clean

Cuando hemos creado mas archivos que no deberían estar en nuestro proyecto o que son archivos que estábamos probando git nos permite borrarlos y dejar los archivos tracker.

`git clean -df --dry-run` -> Borrara los archivos que no estén añadidos al staging area, dry-run lo que hace es mostrarnos el proceso que hará sin hacerlo, una vista previa del comando a ejecutar.

# Git Cherry-pick

Existe un mundo alternativo en el cual vamos avanzando en una rama pero necesitamos en master uno de esos avances de la rama, para eso utilizamos el comando git cherry-pick IDCommit.

cherry-pick es una mala práctica porque significa que estamos reconstruyendo la historia, usa cherry-pick con sabiduría. Si no sabes lo que estás haciendo ten mucho cuidado.

# Reconstruir commits en Git con amend

Amend que en ingles significa remendar, justamente hace eso con el último commit ya que pega o sobrescribe el ultimo.

Ejemplo:
Hiciste cambios al proyecto y finalizaste usando un commit pero te diste cuenta de que algo faltaba; Haces los cambios que faltaban los añades al staging area con `git add`solamente y después haces un `git commit --amend`con lo cual te mandara al editor vim con el mensaje del ultimo commit por si quieres modificarlo.

# Git Reflog

Git nunca olvida, git reflog
Git guarda todos los cambios aunque decidas borrarlos, al borrar un cambio lo que estás haciendo sólo es actualizar la punta del branch, para gestionar éstas puntas existe un mecanismo llamado registros de referencia o reflogs.
.
La gestión de estos cambios es mediante los hash’es de referencia (o ref) que son apuntadores a los commits.
.
Los recoges registran cuándo se actualizaron las referencias de Git en el repositorio local (sólo en el local), por lo que si deseas ver cómo has modificado la historia puedes utilizar el comando:

git reflog
Muchos comandos de Git aceptan un parámetro para especificar una referencia o “ref”, que es un puntero a una confirmación sobre todo los comandos:

git checkout Puedes moverte sin realizar ningún cambio al commit exacto de la ref

git checkout eff544f
git reset: Hará que el último commit sea el pasado por la ref, usar este comando sólo si sabes exactamente qué estás haciendo

git reset --hard eff544f # Perderá todo lo que se encuentra en staging y en el Working directory y se moverá el head al commit eff544f
git reset --soft eff544f # Te recuperará todos los cambios que tengas diferentes al commit eff544f, los agregará al staging area y moverá el head al commit eff544f
git merge: Puedes hacer merge de un commit en específico, funciona igual que con una branch, pero te hace el merge del estado específico del commit mandado

git checkout master
git merge eff544f # Fusionará en un nuevo commit la historia de master con el momento específico en el que vive eff544f

# Buscar en archivos y commits de Git con Grep y log

A medida que nuestro proyecto se hace grande vamos a querer buscar ciertas cosas.

Por ejemplo: ¿cuántas veces en nuestro proyecto utilizamos la palabra color?

Para buscar utilizamos el comando git grep color y nos buscará en todo el proyecto los archivos en donde está la palabra color.

Con git grep -n color nos saldrá un output el cual nos dirá en qué línea está lo que estamos buscando.
Con git grep -c color nos saldrá un output el cual nos dirá cuántas veces se repite esa palabra y en qué archivo.
Si queremos buscar cuántas veces utilizamos un atributo de HTML lo hacemos con `git grep -c "<p>"`.

- `git log-S “cabecera”` --> cuantas veces use la palabra cabecera en
todos los commits.

- `grep` –> para los archivos
- `log` --> para los commits.

# Comandos y recursos colaborativos en Git y GitHub

- `git shortlog -sn` = muestra cuantos commit han hecho cada miembros del equipo.
- `git shortlog -sn --all` = muestra cuantos commit han hecho cada miembros del equipo hasta los que han sido eliminado
- `git shortlog -sn --all --no-merge` = muestra cuantos commit han hecho cada miembros quitando los eliminados sin los merges
- `git blame ARCHIVO` = muestra quien hizo cada cosa linea por linea
- `git COMANDO --help` = muestra como funciona el comando.
- `git blame ARCHIVO -Linea_inicial,linea_final` = muestra quien hizo cada cosa linea por linea indicándole desde que linea ver ejemplo -L35,50
- `git branch -r` = se muestran todas las ramas remotas
- `git branch -a` = se muestran todas las ramas tanto locales como remotas

Alias para git: `git config --global alias.aliasName "comandos a ejecutar"`
