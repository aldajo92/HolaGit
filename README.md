# Introuduccion a Git y Github #
Un buen video para saber que es Git y Github, como referencia, en el siguiente enlace: [Git y Github](https://www.youtube.com/watch?v=DinilgacaWs)

Hay que resaltar que Git y Github no significan lo mismo y es importante el contexto en el que se usan para evitar confusiones.

## Que es Git? ##
Git, es un software de control de versiones diseñado por Linus Torvalds para el manejo de archivos y de proyectos [1]. Su propósito es llevar registro de los cambios en archivos de computadora y coordinar el trabajo que varias personas realizan sobre archivos compartidos [2].

## Que es GitHub? ##
GitHub es una compañía sin fines de lucro que ofrece un servicio de hosting de repositorios almacenados en la nube. Esencialmente, hace que sea más fácil para individuos y equipos usar Git como la versión de control y colaboración. Se define repositorios como aquellos proyectos en git que se encuentran alojados en la nube, que pueden ser privados, o públicos según la modalidad del proyecto.

## Antes de empezar ##
Para poder trabajar con Git y Github es importante que cuentes con lo siguiente:

- Tener una cuenta en [github](https://github.com)
- Tener acceso a una consola.
    - Para windows se recomienda usar powerShell (el cual viene instalado por defecto).
    - Mac y Linux, la consola que viene por defecto.

- Tener instalado git.
    - Para windows, descargar el siguiente programa e instalarlo. [git para windows](https://git-scm.com/download/win)
    - En mac usar la siguiente instrucción en consola:
        ```
        $ brew install git
        ```

    - En ubuntu o debian, usar la siguiente instrucción en consola:
        ```
        $ sudo apt-get install git
        ```

## Crear un primer proyecto ##
Para empezar debemos ubicarnos en nuestra consola en una carpeta vacía, esta carpeta la podemos crear en Documentos con el nombre `FirstProjectGit`. El comando `cd` (para navegar) y el comando `mkdir` (para crear una carpeta) son útiles para estas ocaciones.

Un ejemplo de ello de lo que verás en consola será:

```
C:\Windows\Users\UserName\Documents\FirstProjectGit>
```

Una vez dentro de la carpeta podemos escribir la siguiente instrucción en consola:
```
$ git init
```
Este último comando se encargaría de iniciar un proyecto en git (pero no en github), este se encarga de crear una carpeta oculta con nombre `.git` donde almacenará toda la información sobre nuestros cambios.

Luego definiremos algunos parametros para nuestro proyecto:
```
$ git config user.name "<tu nombre>"
$ git config user.email "<tu email>"
```

A modo de ejemplo:

```
$ git config user.name "Ramón Valdez"
$ git config user.email "ramonValdez@vecindad.com"
```

Dentro de la carpeta, vamos a crear un primer archivo llamado `README.md` el cual contendrá una descripción sobre nuestro proyecto. Agregamos un texto a este archivo, y lo guardamos. Una manera de realizarlo puede ser abrir un block de notas y asegurarnos que tenga el nombre "README.md" en la carpeta donde estamos ubicados. Un ejemplo de lo que puede contener este archivo puede ser algo asi:

```
# Mi primer proyecto #

Este es un template para la descripcion de tu proyecto. El contenido de este texto es para fines ilustrativos.
```

Vamos a crear un primer commit de nuestro proyecto. Commit es el término que asociaremos a aquellos cambios confiables, que hemos definido para los archivos asociados al proyecto. En consola escribimos (cada línea que se muestra a continuacion la ingresamos como una instrucción por separado omitiendo en simbolo `$`):

```
$ git add README.md
$ git commit -m "Creando la Descripción del proyecto"
```

Hasta el momento hemos creado nuestro primer cambio que solo servirá para propósitos locales, es decir, no podremos compartirlo y tampoco hay una copia de respaldo en la nube en caso de que algo falle en el proyecto. Aquí es donde Github aparece como la opción para mantener un respaldo de nuestro proyecto y de nuestros cambios.

Abrimos nuestra cuenta de github y creamos un nuevo repositorio.

![](/media/Capture3.png)

Le damos un nombre a nuestro repositorio (puede ser el mismo nombre de la carpeta que creamos que contiene nuestro proyecto) y dejamos el resto tal como se encuentra.

![](/media/Capture4.png)

Al crear un repositorio vacío en github, veremos algunas instrucciones útiles para poder sincronizar nuestros archivos, algo como esto:

![](/media/Capture5.png)

En nuestro consola, usaremos este comando para saber a cual servicio remoto sincronizaremos nuestro proyecto, el cual denominaremos de aquí en adelante como repositorio.

```
$ git remote add origin "url de tu proyecto terminando en .git"
```

A modo de ejemplo:

```
$ git remote add origin https://github.com/ramonValdez/proyectoGit.git
```

Si por alguna razón te equivocaste o quieres cambiar la dirección url del proyecto, puedes cambiar este parámetro las veces que sean necesarias usando el siguiente comando.

```
$ git remote set-url origin "nueva url de tu proyecto"
```

Luego haremos el primer push, que significa subir o sincronizar los cambios que tenemos en "local" con el proyecto "remoto":

```
$ git push -u origin master
```

El comando anterior solo debe usarse en este formato una única vez, es decir, si no hemos subido ningun cambio antes, nos pedirá sincronizarnos con el proyecto en github de esta manera. Para seguir subiendo en adelante, los commit realizados, usaremos el siguiente comando:

```
$ git push
```

Proponemos el siguiente ejercicio, y es el de modificar el mismo archivo, hacer un commit y luego intentar devolverse al anterior commit. La respuesta se encuentra en los siguientes commandos: 

```
$ git log
$ git checkout HASHCODE
```

Es importante resaltar que aunque podemos usar `commit` y `push` para registrar nuestros cambios, muchas veces queremos experimentar y no afectar nuestro repositorio. Una manera de empezar a modificar nuestros archivos de manera segura es usando una rama o "branch".

Crearemos una rama con el siguiente comando:

```
$ git checkout -b experimento
```

En esta rama creamos un archivo nuevo que se llame main.c, e incluir lo siguiente:

```
#include <stdio.h>

void main(){
    print("hello world");
    return 0;
}
```
Luego, hacemos un commit y un push, y nos vamos a la página en github de nuestro repositorio para verificar en la sección branch.

![](/media/Capture1.png)

Esto nos mostrará nuestras ramas dentro del proyecto. También podemos verificarlo usando el siguiente comando:

```
$ git branch
```

Ya para finalizar esta introducción, podemos mezclar los cambios de nuestro proyecto con el original usando el siguiente comando:

```
$ git checkout master
$ git merge experimento
$ git push
```

Para resumir, la instrucción `checkout` en git se usa para movernos entre ramas. Cuando agregamos `-b` a la instrucción, estamos indicando que vamos a crear una nueva. La instruccion `merge` se emplea para mezclar dos ramas, ubicado en la rama que recibirá los cambios.

El siguiente gráfico, ilustra un ejemplo de como funcionan las ramas:

![](/media/branch.png)

## Proyecto de ejemplo ##

En la parte superior de este repositorio, encontraras un botón que dice fork, el cuál servira para crear una copia de este proyecto y de todos los commits y branch's asociados. Al hacer click sobre el mismo, se creará una copia en tu cuenta. Esta es la manera con la que puedes experimentar sobre cualquier proyecto que encuentres en github sin afectar ni requerir permisos, permitiendo tener una versión propia del proyecto.

![](/media/Capture2.png)

Una vez que realizas el fork, el nombre del repositorio tendra el mismo nombre, pero se encontrará asociado a otro usuario.

El primer ejercicio consistirá en modificar el archivo `main.c` de la carpeta src, donde agregaremos algunas funciones para realizar operaciones matemáticas.

Luego haremos un commit y un push, para subir nuestros cambios.

Si realizaste todo tal como se indicó en esta guía, felicitaciones, ahora tienes dos repositorios para compartir.

## Referencias ##
[1] [Que es Git, Codigo facilito](https://codigofacilito.com/articulos/que-es-git)

[2] [Git, Wikipedia](https://codigofacilito.com/articulos/que-es-git)
