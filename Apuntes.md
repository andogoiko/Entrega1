## Aquí está el chuletario de los comandos de distintos lenguajes y programas:

# CMD:

## Comandos básicos de cmd para utilización básica:

- code .: abre el Visual estudio en el directorio que estés.

- rd /s /q: sirve para borrar el directorio en el que te encuentres

- mkdir: crea un directorio en el directorio que te encuentres

- dir: te dice los ficheros.

- tree: te dice los ficheros que hay de manera más gráficas.

- %1: sirve para parametrizar.

- cd (inserta nombre de directorio): muévete hacia el directorio espacificado.

- cd ..: sirve para volver al directorio anterior

- echo "container": muestra un mensaje en pantalla.

- echo "container" > vertedero.txt: añade un texto al archivo vertedero.txt

- echo "San Marcos" >> vertedero.txt: añade un texto al archivo vertedero.txt sin borrar lo que había anteriormente.

- type vertedero.txt: muestra en la pantalla el contenido de vertedero.txt

- copy (archivo original) (nombre del nuevo archivo): copia un archivo y dale un nombre a la copia.

- copy (archivo original y su ruta) (nombre del nuevo archivo y la ruta nueva): copia un archivo de una ruta y dale un nombre a la copia en una ruta nueva.

- ren (nombre viejo) (nombre nuevo): cambiar nombre de un archivo

- move (archivo y su ruta) (ruta): mueve a donde quieras el archivo selecionado

# Markdown

## Aquí van varios comandos de markdown para saber cómo lograr decorar los apuntes:

- crear un párrafo nuevo: pulsar 2 veces intro

-  Encabezados: #1, ##2 ,###3 ,####4 ,#####5 ,######6

- Citas: colocar > al comienzo de un bloque y colocar dos > para hacer citas anidadas

- Hacer listas desordenadas: utiliza *, - o + para hacerlas

- Hacer listas ordenadas: has de poner 1.

- listas anidadas: colocar 4 espacios en blanco antes de hacer la lista

- Códigos bloque: colocar tres ~

- Reglas horizontales: colocar 3 *, - o _

- Elementos en línea: *para cursiva* o _para cursiva_ y **negrita** o __negrita__ también ***cursiva y negrita*** o ___cursiva y negrita___

- Links o enlaces: [texto enlazado](link)

- código: poner el texto entre acentos graves `tal que así` o al principio de un párrafo 4 espacios en blanco

- añadir imágenes: ![nombre de la imagen](link de la imagen)

# GIT:

## Comandos simples para subir y bajar archivos y tenerlos trackeados:

- git config: el siguiente comando se usa para establecer un email.

- git version: sirve para ver que versión de git hay instalada.

- git clone https://github.com/andogoiko/git-youtube.git: crea copia del repositorio en tu ordenador.

- git pull https://github.com/andogoiko/Entrega1.git: haz una copia del repositorio en tu ordenador (solo se copian los archivos dispares).

- git init: iniciar el git

- git status -s: utilizado para saber que archivos no tienen seguimiento.

    - git add .: el comando añade todos los archivos al área temporal.

    - git add *.extensión_de_archivo: el comando añade todos los archivos del tipo que se ha elegido.

    - git add archivo: utilizado para añadir u archivo al área temporal.

    - git remote add origin "aquí va un link de tu repositorio": sirve para añadir archivos en tu rama de origen

- git commit -m "mensaje": después de guardarlo en el área temporal este comando lleva al siguiente nivel el archivo junto con un mensaje y guarda el momento exacto.

- git log --online: sirve para ver los identificadores de los commit

- git push: con este comando se suben los archivos a github (antes debes haber realizado git add y git commit en su orden respectivo).

- push -u origin master: sube los archivos de tu rama principal (tu rama master) a la rama de origen de github (origin)

- git reset --soft (identificador): sirve para viajar a un archivo guardado según su identificador, no se borrarán los commits anteriores.

- git reset --mixed (identificador): sirve para viajar a un archivo guardado según su identificador, todo lo que se edite aquí no se guardará.

- git reset --hard (identificador): sirve para viajar a un archivo guardado según su identificador, se borrarán los commits anteriores.

- `doskey /history: una vez puesto este comando aparecerán todos los comandos que han sido utilizados en una lista.`

## Comandos para andar por las ramas:

- git branch: utilizado para mirar las ramas que tengas creadas

- git branch "nombre": crea una nueva rama con el nombre elegido

- git checkout "nombre": muévete a la rama nombrada

- git merge: sirve para fusionar dos ramas

- git rebase: recopila uno a uno los cambios confirmados en una rama, y reaplicarlos sobre otra.