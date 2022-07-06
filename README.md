## Un poco de teoria
Los archivos para git los toma como rastreados o sin rastrear
Es decir, los que está tomando en cuenta.

Git tiene 3 estados
El area de trabajo     -     El stage/limbo      -  El directorio git
Archivos modificados   -   Archivos preparados   -  Archivos confirmados

------------------- git add -> -------------- git commit ->

# Comandos básicos de git

## Git: Es local
Sea _nombre_ el nombre del archivo, _rama_ la rama en cuestión y _commit_ algún commit

#### Comandos básicos de gran utilidad

  * **git config** configuración de git, de prefrencia con --global para aplicar
  a todos los repositorios. --list para ver la config
  Con user.name, user.email, alias.[nuevo comando] 'comando'

  * **git init**: Inicia un repositorio local

  * **git add nombre**: Empieza a rastrear archivos así como prepararlos para el stage

  * **git commit -m "mensaje"**: Confirma los cambios al repositorio de git .git
  Se puede poner -a para saltarnos el git add
  --amend sobreescribe el mensaje del commit

  * **git status**: Muestra el status de los archivos, -s para abreviar

  * **git restore**: --Vuelve un paso atrás el estado del area de trabajo (peligro)
  --staged Vuelve un paso atrás pero del staged
  
  * **git log**: Muestra el historial de versiones de la _rama_, **no** de todo el repositorio
  Algunas banderas son   
  * -p muetras la diferencias
  * -n muestra los ultimos n commits
  * -stat muestra stadisticas
  * --graph muestra el grafo
  * --since=[time ]
  * --until
  * -pretty le da un formato bonito
  Algunas banderas para pretty son 
  * oneline para que se muestre en una linea
  * short lo hace corto
  * format añade formato
  * %h hash abreviado
  * %a arbol abreviado
  * %an nombre del autor 
  * %ae email del autor
  * %ar fecha del commit



#### Trabjando con ramas
   * **git branch rama**: Crea una rama de trabajo
   * **git checkout rama**: Cambia a la rama de trabajo
    * Así git checkout master: cambia a la rama principal
   * **git checkout -b rama**: Crea una rama y se cambia a ella
   * **git branch -d rama**: borra la rama
   * **git diff rama**: Muestra la diferencia de la versión actual y el último _commit_.
   * **git diff rama1 rama2**: Muestra las diferencias entre dos commits especificos
    * La salida se puede redirigir poniendo >~/nombre.diff al final del comando.
    * Dicho comando diff puede recibir archivo, rama o commit 
   * **git clean -x -f -d**: Limpia toda la rama de trabajo  borraando todos los archivos no agregados al repositorio
   

## Github: Es remoto

##### Los principales comandos son
  * **git clone htpps://github.como/usuario/nombre:** Clona el repisotorio dado
  * **git remote add origin https://github.com/usuario/nombreDelRepo.git**: Sincroniza por medio de HTTPS (En las ultimas versiones es con SSH)
  * **git remote add origin  git@github.com:usuario/nombreDelRepro.git**: Sincorniza por medio de SSH
  * **git pull**: Actualiza tú repositorio local al commit mas reciente
  * **git merge rama**: Fusiona la rama activa con la rama indicada
  * **git push -u origin master**: Sube los cambios al repositorio en linea
  * **git push origin rama**: Subo la rama que indico a la rama donde estoy (recomendable usar _git status_ y _git diff_ )
  * **git reset commit**: elimina todos los commits después del señalado