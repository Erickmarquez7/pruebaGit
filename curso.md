4.- 
5.-
6.-
7.-

#Clase 1
Git guarda el historial con "capturas".
Para esto tenemos las 3 áreas.

Los respectivos comandos son 

`git init` Inicia un repositorio
`git add archivos` Añade los cambios al staged
`git commit`: Confirma los cambios del staged
- `-m "msg"` para agregar mensaje
- `-a` para saltarse `git add`
- `--amend` sobreescribe el mensaje

Pero como son las "fotos" tenemos que poner quién toma la foto.

`git config` configuración de git
- `--global` para hacer cambios en TODOS los repositorios de la compu
- - `user.name nombre` Configuramos el nombre del autor
- - `user.email correo` Configuramos el correo del autor
- - `--list` Para ver la configuración global
- `--list` Solo veríamos la del repositorio en el que estamos

¿Cómo sabemos en que estado se encuentran nuestros archivos?
`git status` Muestra el estado de los archivos
- `-s` Lo muestra de manera simplificada con letras
La derecha significa que **no** está en el staged
La izquierda que ya está en el staged
**A** Recién añadido
**-M** Modificado pero no preparado
**M-** Modificado y listo para hacer commit
**MM** Ambas de arriba
**-D** Borrado pero no preparado
**D** Borrado y listo para hacer commit
**??** Archivo sin seguimiento


####Ejercicios
Jugar con los archivos y conseguir que aparezcan todos los estados.

#Clase 2
Queremos saber cuáles fueron los cambios
`git diff archivo` Muestra las diferencias entre el área de trabajo y lo que estaba antes, es decir, lo recíen añadido
Una vez que apliquemos el `git add`, este comando ya no mostrará nada pues el archivo está en el staged, para eso:
- `--staged` muestra las diferencias entre lo que está en el staged y el último commit, es decir, será incluido en el commit
Podemos redirigir la salida con `> diferencia.diff`

Para restaurar archivos a su forma anterior
`git restore archivo` Restaura el archivo 
- `-- staged` Lo saca del staged
`git rm archivo` elimina el archivo, además lo prepara en el staged, es decir
ejcuta `add` de manera automatica

Cuando cambiamos el nombre de aun archivo git no lo rastrea explicitamente
por ello tiene un comando `git rm` que basicamente son los siguiente comando juntos
`mv archivo-antes archivo-ahora`
`git rm archivo-antes`
`git add archivo-ahora`

El segundo comando NO es igual a `restore` ya que restore solo lo saca del staged
mientras que `rm` elimina el archivo

Historial
`git log` muestra el historial de commits con hash, nombre y correo del autor
log puede recibir varias banderas y distintos formatos para que se vea más bonito, algunos son 
- `-n` muestra los últimos *n* commits
- `-p` nos muestra las diferencias entre commits
- `--oneline` lo simplifica en una linea
- `--graph` añade un una representación grafica
- `--all` nos muestra todas las ramas
- `--since=n.weeks` o en específico `since='2020-12-10'`
- `--until='2022-10-10'`
Además podemos hacerlo con formato 
- `--pretty="format: "`
- - `%h` muestra el hash
- - `%t` muestra el árbol
- - `%p` hash del padre
- - `%an` nombre del autor
- - `%ae` email del autor
- - `%ar` fecha

#####Ejemplo
`git log --pretty="format: %h - %an, : %s"`

####Ejercicios
Jugar con los comandos y anotar las diferencias antes y después de cada comando

#Clase 3
`git log` puede llegar a ser bastante largo, para ello utilizamos alias

`git config --global alias.new 'comando'`

¿Qué es una rama?
Los commits son como "fotos" de como lucía el trabajo hasta ese entonces, las ramas es el historial de cambios de todas esas fotos. Una rama es básicamente un apuntador a una confiramción (commit).
`git branch nueva` Crea una nueva rama
`git checkout rama` Cambiamos de rama
Podemos utilizar `git checkout -b rama` para crear una rama y saltar a ella

A veces queremos localizar más rápido estos commits
`git tag v0` Añade una etiqueta ligera al commit actual
- `-a` hace la etiqueta anotada
- `-m "msg"` añade el mensaje
- `ABC123` el hash abreviado para añadir el alias a ese commit



####Ejercicios
#Clase 4
####Ejercicios

------------------------------------------------------------------------------------
| Ignorar archivos
Creando un archivo .gitignore y poniendo los que no queremos que tome en cuenta
*.[abc] ignora los que terminan en .a || .b || .c, o sea los [] lo hacen or

*.~ ignora los que terminen en ~ 
*.java los que terminan en java, es decir toda la cadena

? Caracter cualquiera

[0-9] Cualquier caracter entre ellos

a/**/z Cualquier directorio entre ellos, anidados a/z, a/b/c, a/b/f/z

#comentario en tal archivo xd
/comenzando así evita la recursividad
Así al final especifica un directoio/
!Niega la expresión

ejemplos:

#niega todos los javac
*.javac 

#excepto este, aun cuando se especificó anteriormente
!main.javac

#ignora solo el archivo ridmi de la raiz, mas no de la subcarpetas
/ridmi

#todos los archivos de la carpeta images
/images

#ignora doc/notes.txt, pero no doc/sub/notes.txt
doc/*.txt

#para eso es, ignora TODOS los archivos .txt 
doc/**/*.txt

-- Es recomendable hacer esto al iniciar un repoxd

| Eliminar archivos
Es necesario eliminarlos del staged
git rm 
Lo elimina del work directory así como del staged, es decir, lo prepara

git rm --staged || --cached <archivo>
Lo elimina solo del stage, se mantiene en el work directory

Admite expresiones regulares

Podemos renombrar archivos con 
git mv

git log --pretty="format: %h - %an, : %s"


-----------------------------REMOTOS--------------------------
Remoto es basicamente el servidor en linea, por lo general es origin
git remote pa ver los remotos 
-v para ver los link asociados

git remote add [nombre] [url] para añadir remoto
git remote add origin https://marquezErick/....

git fetch [nombre-del-remoto] trae todos los cambios que aun no tengo en dicho remoto
git fecth origin

*Cuando clonamos un repo git clone, el comando automaticamente añade el remoto origin
clone es como un git init; git remote add origin; git fetch, todo en uno xd

git fecth Solo trae la info, NO la mezcla

git pull trae y combina dichos cambios a la rama que configuré

git push [nombre-remoto] [nombre-rama] envio los cambios al servidor de mi rama master
git push origin master

git remote show [nombre-rama] muestra mas detallada 

git remote rename [anterior] [nueva] renombra el remoto

{Cambio extras para que diverga la rama equis dedede}
