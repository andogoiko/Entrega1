# `AQUÍ VAN VARIAS PREGUNTAS Y RESPUESTAS INTERESANTES SOBRE GIT`


## `1. ¿Cómo puedo deshacer el último commit en Git?`

El comando es git reset <commit>

Para deshacer específicamente el último commit puedes usar HEAD~1

Por ejemplo para volver al commit anterior puedes usar el sgte comando:

git reset HEAD~1

El parámetro --mixed permite mantener los cambios en el working tree para que puedan ser modificados luego, sin embargo al ser el modo por defecto no es necesario.

En este caso me parece la opción más adecuada ya que quieres corregir el commit así que necesitas revertir el index para corregir los cambios.

Algunos de los parámetros opcionales son:

    --soft no modifica ni el working tree ni el index. Solo cambia el HEAD al commit indicado.
    --mixed revierte el index pero no el working tree de modo que se mantienen los cambios listos para ser modificados y posiblemente commiteados de nuevo. Esta es la opción por defecto.
    --hard Revierte el index y el working tree de modo que los cambios se pierden totalmente.


# `2. ¿Cómo cambiar el mensaje de un commit?`


La opción más práctica y rápida es usar:

git commit --amend

Tras lo cual se te abrirá el editor para que puedas modificar el mensaje.

Si quieres escribir algo totalmente nuevo, puedes decir directamente:

git commit --amend -m "Este es el nuevo comentario"



# `3. ¿Cuál es la diferencia entre 'git rebase' y 'git merge'?`


Resumen para lectores ávidos de conocimiento rápido: con git rebase tendrás un historial más claro, por lo que suele ser la opción preferida.

Cuando haces git rebase:

    los commits locales se eliminan de la rama temporalmente.
    se ejecuta un git pull.
    los commits locales se insertan nuevamente.

Esto quiere decir que todos tus commits locales aparecen al final, después de los commits remotos. Esto es, si haces git log, los commits de la rama que has rebasado aparecen como si fueran más antiguos, independientemente de cuándo se hicieran.

Supongamos que tienes 3 commits A,B,C:

![ABC](https://i.stack.imgur.com/lJRq7.png)

Entonces viene Daniel y crea un commit D. Luego Enrique crea un commit E:

![A-B-C-D-E](https://i.stack.imgur.com/pK7Zb.png)

Obviamente, este conflicto debe ser resuelto de alguna forma. Para ello hay dos maneras:

MERGE:

![A-B-C-D-E-M](https://i.stack.imgur.com/9Ul5w.png)

Ambos commits D y E aún están allí, pero creamos un commit de unión (merge commit) M que hereda los cambios de ambos commits D y E. Sin embargo, esto crea la estructura en forma de diamante, que a mucha gente confunde.

REBASE:

![A-B-C-D-E-R](https://i.stack.imgur.com/TvXuJ.png)

Creamos un commit R, cuyo contenido es idéntico al del commit M descrito arriba. Sin embargo, nos cargamos el commit E como si nunca hubiera existido (se ve con los puntitos, en la línea evanescente). De acuerdo con esta anulación, E debería ser un commit local de Enrique y no debería haber hecho push a ningún repositorio. La ventaja de este método es que se evita la forma de diamante y el historial permanece lineal, que es algo que la mayoría de los desarrolladores agradecen.

De forma menos visual pero más descriptiva, podemos referirnos a ello de la siguiente forma:

    git-rebase – Genera una serie de commits secuencialmente, de modo que puedan aplicarse directamente sobre la cabeza del nodo.

Cuando haces un rebase en tu rama, le estás diciendo a Git que haga como si hubieras cambiado de rama (checkout) de una forma limpia y que luego empezaste a trabajar a partir de allí. Esto convierte los cambios en algo limpio y conceptualmente simple que otra persona podrá revisar. Puedes repetir este proceso otra vez cuando hay nuevos cambios en la otra rama: siempre terminarás con una serie de cambios limpios en la cabeza de la rama.

    git-merge – Une dos o más historiales de desarrollo

Cuando haces un merge de una rama en la tuya, juntas el historial de ambas. Si después haces esto otra vez, empezarás a crear una serie de historiales intercalados: algunos cambios de Daniel, algunos de Enrique, algunos de Daniel... lo que puede ser lioso.

Así, hablando en plata, es como si dijéramos "tenemos dos padres, queremos un hijo".


# `4. ¿Cómo ver qué archivos son diferentes entre 2 ramas con Git?`


Básicamente el comando para ver las diferencias entre dos branches es:

$ git diff branch1..branch2

Para listar qué archivos han cambiado entre dos branches puedes usar --name-status:

$ git diff --name-status branch1..branch2

Para mayor detalle, puedes usar difftool con alguna herramienta. Por ejemplo yo la uso con Meld:

![muchotexto](https://i.stack.imgur.com/W4puv.png)



# `5. ¿Qué es la rama master en git?`


Cuando clonas un repositorio clonas también sus ramas, no sólo la master (la maestra, la que se crea por defecto), pero las guarda dentro del repositorio "remoto" y no la hace "local" hasta que usemos checkout.

Usando git branch -a podrás ver todas y usando git checkout todo podrás cambiar a la rama todo y ver que cambia el contenido del repositorio, momento a partir del cual también podrás ver esa rama como local usando git branch -a.


# `6. ¿Por qué no es posible almacenar un directorio vacío en git?`



Los repositorios se usan para almacenar un historial de los cambios en los ficheros.

Un directorio como tal no va a tener historial de cambios, luego no tiene demasiado sentido que un repositorio almacene un directorio vacío.

Hay que tener en cuenta que los repositorios suelen crear directorios únicamente para replicar la organización de los ficheros que se suben. Es decir, un directorio únicamente sirve como medio para almacenar ficheros. Si un directorio está vacío pierde su sentido dentro del repositorio.



# `7. Eliminar una rama Git tanto el local como en remoto`


A partir de Git v1.7.0, puedes eliminar una rama remota utilizando:

git push origin --delete <NombreRama>

que es más fácil de recordar que

git push origin :<NombreRama>

que fue añadido en Git v1.5.0 “para eliminar una rama remota o una etiqueta”.

Por consiguiente, la versión de git que has instalado impondrá si necesitas utilizar la sintaxis más fácil o la más difícil.


# `8. ¿Por qué “git diff” no funciona sin antes hacer un “git fetch”?`


Debes tener en cuenta que git diff solo funciona en local, es por esto que debes tener primero la "rama" origin/master actualizada (lo cual haces con fetch).

Puedes leer al respecto en Learn the workings of Git, not just the commands en inglés.

Recuerda también que git fetch solo descarga los últimos cambios del repositorio, no los aplica, así que es seguro hacer git fetch antes del git diff.

![git-data-transport-commands](https://i.stack.imgur.com/B55yc.png)


# `9. ¿Como recuperar una rama borrada de git?`



Puedes intentar:

git fsck --full --no-reflogs | grep commit

Para encontrar el commit HEAD de la rama borrada.

Si quieres encontrar qué commit es el correcto puedes hacer uso de git show

Y una vez tengas el mensaje de commit localizado, crear la rama de nuevo con un git branch <uid>


# `10. ¿Cómo deshacer 'git add' antes de confirmar?`


Para deshacer el staging que hizo el git add ., puedes hacer:

git reset

Verás que los archivos no cambian, es solo que deshaces el staging en preparación para el commit.