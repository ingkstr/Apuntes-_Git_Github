APUNTES GIT Y GITHUB
====================

 * Git
   * [Los tres estados de Git](#Los-tres-estados-de-Git)
   * [Instalación de Git](#Instalación-de-Git)
   * [Configuración inicial](#Configuración-inicial)
   * [Creación de repositorio](#Creación-de-repositorio)
   * [Revisión de estatus](#Revisión-de-estatus)
   * [Manejo de archivos en stagingg](#Manejo-de-archivos-en-staging)
   * [Commit a git directory](#Commit-a-git-directory)
   * [Revisión de log de versiones](#Revisión-de-log-de-versiones)
   * [Taggear versiones](#Taggear-versiones)
   * [Diferencia entre versiones](#Diferencia-entre-versiones)
   * [Reset de versiones](#Reset-de-versiones)
   * [Cambio de editor de Git](#Cambio-de-editor-de-Git)
   * [Manejo de ramas](#Manejo-de-ramas)
   * [Mezcla de ramas y solución de conflictos](#Mezcla-de-ramas-y-solución-de-conflictos)
   * [Rebase](#ebase)
   * [Stash](#Stash)
   * [Cherry Pick](#Cherry-Pick)
 * Github
   * [Acceso a proyectos preexistentes](#Acceso-a-proyectos-preexistentes)
   * [Ligar un repositorio Github a un repositorio local](#Ligar-un-repositorio-Github-a-un-repositorio-local)
   * [Copiar archivos de Github a Git](#Copiar-archivos-de-Github-a-Git)
   * [Enviar última versión local a Github](#Enviar-última-versión-local-a-Github)
   * [Otros conceptos](#Otros-conceptos)
   * [Templates recomendados](#Templates-recomendados)
   * [Gitignore](#Gitignore)
   * [Github pages](#Github-pages)
   * [Desktop Github](#Desktop-Github)

# GIT #

## Los tres estados de Git ## 
Estos son los tres estados de Git: 
 
 - Working Directory: Es el entorno local de trabajo (la PC)
 - Staging Area. Esta es una área de preparación. 
 - Git Directory (repository): Es la versión almacenada

Estos tres estados representan el ciclo de vida de nuestros archivos dentro de la plataforma. 
 
`Working directory` ---STAGE FILE---> `Staging area` ---COMMIT --> `Git directory`
  
 
## Instalación de Git ##
 
Se descarga de la URL https://git-scm.com 

Se recomienda instalar zsh y oh-my-zsh para mejor vision del entorno de Git. 
 
## Configuración inicial ##

Para obtener la versión actual

> git --version 

Se deben insertar los siguientes parámetros

> git config --global user.email ingkstr@gmail.com 

> git config --global user.name "Jose Emanuel Castelan" 

> git config --global color.ui true 

## Creación de repositorio ##

Dentro de la carpeta de un proyecto se usa el siguiente comando

>cd PROYECTO

> git-init 

Al crear, modificar o eliminar un archivo, aparecerá un símbolo `✗` avisando de que no se ha cargado la versión más reciente

Para borrar un repositorio usamos este comando (esto dado a que el repositorio ocupa una carpeta oculta `.git`)

> rm -rf .git 
 
## Revisión de estatus ##

Se usa el siguiente comando 

> git status 

## Manejo de archivos en staging ##

Se puede agregar archivo por archivo

> git add index.html 

O se agregan todos los archivos de la siguiente manera

> git add .

Para quitar archivos de staging se usa

> git rm --cached index.html 

Para eliminiar archivos de staging y directorio local 

> git rm -f index.css 

Para verificar si un archivo se puede ingresar a staging sin agregarlo 

> git add -n index.css

## Commit a git directory ##

Teniendo los archivos listos a crear una nueva versión, se usa el siguiente comando

> git commit -m "Descripción de la versión"

Para agregar archivos a la versión actual sin crear una nueva, usamos el siguiente comando

> git commit --amend 

## Revisión de log de versiones ##

Se usa el siguiente comando

> git log

Las versiones aparecen de la siguiente manera

```
commit 7f6f97ed02aa5d5aeb97630119bccf8d2d459287 (HEAD -> masterr)
Author: Jose Emanuel Castelan <ingkstr@gmail.com>
Date:   Tue Jan 29 18:49:59 2019 -0600

    Versión 2

commit 238851e36064984a0e3adb6f770e1034defa2241
Author: Jose Emanuel Castelan <ingkstr@gmail.com>
Date:   Tue Jan 29 18:47:31 2019 -0600

    Versión 1

```

Delante del commit aparece un `hash` que sirve para identificar cada versión

Para visualizar el log en una línea por versión usamos el siguiente comando

> git log --oneline 

Para mostrar las ramificaciones en el árbol del repositorio usamos:

> git log --oneline --graph 

Para revisar los últimos 3 commits usamos

> git log -3

Para ver el último commit

> git log -1

## Taggear versiones ##

Se usa la siguiente sintaxis (aquí se crea una versión 1.0)

> git tag -a 1.0 -m 'Version estable inicial' 

Se enlistan de la siguiente manera las versiones tageadas

> git tag -l 

Para marcar un tag a una versión vieja, se identifica el hash y se usa la siguiente sintaxis

> git tag x.x [HASH]

Para borrar un tag

> git tag -d x.x 

## Diferencia entre versiones ##

Para comparar versiones se usa el comando `gi diff`

Para ver la diferencia entre la versión actual y una específica se usa el siguiente

> git diff [SHA]

Para comparar dos versiones específicas se usa

> git diff [SHA1] [SHA2]

## Reset de versiones ##

Se usa `git reset` para resetear versiones. Hay tres tipos:
 
 - `SOFT` : Regresa una versión fija en Git repository a staging

> git reset --soft [ULTIMO HASH A CONSERVAR]

 - `MIXED` : Regresa una versión fija en Git repository al Working Directory

> git reset --mixed [ULTIMO HASH A CONSERVAR]

 - `HARD` : Toma una versión fija y la elimina, así como los archivos existentes. También se usa para eliminar archivos en moo staging.

> git reset --hard [SHA]

Para recuperar los archivos eliminados por un hard reset, se debe conservar el SHA y se usa el siguiente comando

> git reset --hard [SHA]

Para retirar archivos de modo staging y devolverlos a working, usamos

> git reset HEAD archivo 


## Cambio de editor de Git ##

Usamos estos comandos

> git config --global core.editor vim //Para editor vim

> git config --global core.editor "atom --wait" //Para editor atom
 
## Manejo de ramas ## 

Debemos tener en cuenta que todos los repositorios comienzan con la rama master

Para crear ramas se usa 

> git branch [nombre_rama]

Para listar las ramas

> git branch -l

Para eliminar ramas se usa
 
> git branch -d [rama] // eliminacion de ramas 

> git branch -D [rama] // eliminacion forzada de rama 

Para cambiar el nombre de una rama se usa 

> git branch -m [rama] [nuevo nombre]

Para entrar a una rama o versión se usa 

> git checkout [rama] // entra a la rama deseada

> git checkout [SHA] // entra a una version deseada 

> git checkout master // version actual master 

Para crear una rama y acceder inmediatamente se usa

> git checkout -b [rama] 

## Mezcla de ramas y solución de conflictos ##

Debes colocarte en la rama que desees que reciba los cambios 

> git checkout [rama-destino]

Se usa el siguiente comando
 
git merge [rama origen] 
 
 
Al haber fast-forward es que el cambio se hizo con la version inmediata a la que ya existia 
 
Al mezclar con una versión no imediata, abrira el editor para confirmar los cambios (solo añadiendo). 
 
Si los cambios hacen conflicto entre si, no los hará y podras revisarlos con atom. 

Git fusiona tus archivos para que los coordines y al final debes hacer un git commit con los nuevos cambios 
 
## Rebase ## 
SE RECOMIENDA USAR SOLO CUANDO SE TRABAJA LOCALMENTE 

Permite reescribir la historia de tu proyecto 
 
> git rebase [rama] 

Para reescibir la versión metiendo un comentario

> git rebase -i [rama] 


## STASH ## 
  
Si requiere continuar cambios interrumpidos por hacer trabajos en otra rama, se usa git stash. 

Solo se puede hacer stash con elementos agregados a staging
 
> git stash 

Al hacer `git status` no aparecerán los cambios, así que para consultar las versiones pendientes se usa

> git stash list

Para borrar un cambio pendiente se usa

> git stash drop stash@{N} 

Para retomar un trabajo al inicio de la cola de la lista, se usa
 
git stash apply

O para tomar un trabajo específico se usa

> git stash apply stash@{3}

## Cherry Pick ##
 
Si se necesita mandar un commit de un arbol a otro, primero se pasa a la rama destino 

> git checkout [rama destino]

Y después se usa este comando

> git cherry-pick [SHA a traspasar] 
 

# GITHUB #

## Acceso a proyectos preexistentes ##

 - `Fork` : me deja copiar un proyecto a mi cuenta github y poder hacer los cambios que querramos 

 - `Clone or download` Te permite copiar o descargar un proyecto. Obtienes una URL en SSH o HTML para consultarlo, así como descargarlo en ZIP.
 
 
Para poder usar proyectos en tu computadora e interactuar con tu cuenta Github, debes generar una llave pública

> ssh-keygen -t rsa -b 4096 -C "micorreo@gmail.com" 

Después debes copiar el contenido de la llave. De no ser posible, se usa un cat para revisarlo y copiar manualmente

> pbcopy < ~/.ssh/id_rsa.pub 

Al final, ir a `Settings` -> `SSH and GPG keys` -> `New SSH key` y agregar la llave.
 
 
## Ligar un repositorio Github a un repositorio local ##
 
Para clonar un proyecto (habiendo configurado previamente los permisos

> git clone [url ssh de proyecto]

Para ligar un repositorio github a nuestro repositorio local

> git remote add origin [URL SSH repo github] 

Por convención, la conexión la debemos llamar siempre `origin`

Para consultar estatus de los repositorios remotos

> git remote -v 

Para desconectar un proyecto

> git remote remove origin 

## Copiar archivos de Github a Git ##

Hay dos formas

 - `Forma 1`

> git fetch origin master
> git merge origin/master 
> git merge origin/master --allow-unrelated-histories 

- `Forma 2`

> git pull origin master 

## Enviar última versión local a Github ##

Para enviar versión final de master

> git push origin master

Para mandar la última versión de un árbol se usa

> git push origin [rama]

Para enviar tags creados

> git push origin master --tags 

## Otros conceptos ## 

 - `Star` -> Likes del proyecto 
 - `Insight` -> Estadisticos 
 - `Settings` -> crea colaboradores, branches existentes 
 - `Pull request` -> cambios propuestos por otros programadores 
 - `Issues` -> Reporte de fallas de un proyecto
 - `Protección de commits indeseados` : Ir a `Settings` -> `Branch` -> `Branch protection rules` -> Activar Require pull request reviews before merging. 
 - `Projects` Usado para promocionar avance de nuevos features usando metodología Scrum
 - `Milestones` : Conjunto de fallas y mejoras agrupadas. Ahi se pueden asignar issues reportados

## Templates recomendados ##

 - `issue_template.md` - Template para reporte de fallas 
## ¿Cómo puedo replicar el problema? 
Por favor, explica como replicar el problema paso a paso y en que S.O. ocurre 
## En que versión ocurre??? 
Si este problema ocurre en todas las versiones, por favor, aclaralo 
```
 
 - `pull_request_template.md` - Usado para reportar nuevas mejoras
 
```
# Descripcion 
Que ha cambiado? 
 
- [ ] Front end 
- [ ] Backend 
- [ ] Server config 
 
# Como puedo probar los cambios 
En que url y que forma lo puedo ver 
```

## Gitignore ##

Permite que no carges archivos sensibles a tus repositorios como bases de datos, configuraciones, caches, etc.

Se debe crear un archivo `.gitignore` y capturar en el los archivos no deseados a cargar.

> touch .gitignore

Puedes consultar la página www.gitignore.io con plantillas de gitignore para cada lenguaje de programación

## Github pages ##

Se pueden publicar páginas estáticas de un proyecto. OJO. DEBE TENER UN INDEX.HTML
 
Se debe ir a `Settings` -> `Github pages` y eliges la rama a publicar.

Al final, se genera una URL donde se consulta tu página. Aunque puedes cargar un dominio. Se recomienda conseguirlos de namecheap.com.
 
## Desktop Github ##

Existe una versión de Github para PC y se puede descargar en https://desktop.github.com/ 
 

 
