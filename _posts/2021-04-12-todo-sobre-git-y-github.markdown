---
layout: post
title:  "Todo lo que necesitas saber sobre Git y Github"
date:   2021-04-12 22:03:46
---

### ¿Qué es Git?

Git corresponde a un **sistema de control de versiones** desarrollado por Linus Torvalds.

No olvidemos que cuando hablamos de **control de versiones**, nos referimos a la gestión de los diversos cambios que se realizan sobre un proyecto (subir código a la nube, añadir alguna parte o simplemente editar algo que no funciona correctamente, entre otros).

Por lo tanto, un sistema de control de versiones serían todas las herramientas que nos permiten hacer esas modificaciones antes mencionadas sobre nuestro trabajo, haciendo más fácil la administración de las distintas versiones.

### Git en el mundo

Git es usado por grandes empresas ya que esta herramienta permite que muchas de las aplicaciones que usamos hoy en día sean tal y como las conocemos. Algunas de estas empresas, que de seguro las conocerás, son las siguientes:

* Facebook
* Twitter
* Netflix
* Google
* LinkedIn

Estas corresponden a empresas que venden productos de Internet, por lo que hoy en día su uso es pan de cada día. Sin embargo, Git también tiene presencia en los equipos de trabajo que desarrollan sistemas operativos para los dispositivos, tales como:

* Microsoft
* Android
* Linux

Incluso el software que nos ayuda a crear más software utiliza Git:

* Ruby on Rails (Framework de Ruby para el desarrollo web)
* PostgreSQL (Gestor de Base de Datos)
* Eclipse (IDE para crear aplicaciones en Java)

Y no cabe duda de que hay muchos otros ejemplos de equipos de trabajo que utilizan Git no solo en el desarrollo de software, sino también de contenido y productos profesionales.

### Instalación y configuración de Git

En Sistemas Operativos como Ubuntu o Mac OS Git ya viene instalado, por lo que solo debemos configurarlo. Para ello abrimos la terminal y tecleamos lo siguiente:

{% highlight r %}
$ git config --global user.name "YOUR NAME"
$ git config --global user.email "YOUR@EMAIL.com"
{% endhighlight %}

En **YOUR NAME** debe ir nuestro nombre y en **YOUR@EMAIL.COM** el correo que utilizamos o utilizaremos para nuestra cuenta de Github.

### Flujo de trabajo

Git está compuesto por tres estados o árboles en los que se pueden encontrar los archivos de nuestro proyecto:

1. **Working directory**: Directorio de Trabajo, contiene nuestro archivo o conjunto de archivos del proyecto.
2. **Staging area**: Área de Preparación, también es conocida como **index** y actúa como una zona intermedia en donde escogeremos qué archivos están listos para pasar al siguiente estado y/o cuales no lo están por el momento.
3. **Git directory**: Directorio de Git, también se le conoce como **head** y corresponde al repositorio donde se encuentra el registro de todo nuestro proyecto (commits).

<img src="{{ site.baseurl }}/assets/img/EstadosGit1.jpg">

Aquí es donde aparece una nueva palabra: **commit**. Un commit corresponde a la acción de guardar o subir un archivo o conjunto de archivos al Directorio de Git (head).

### Primeros commits y viajes en el tiempo

1. `git init`: Se utiliza para inicializar un repositorio local.
2. `git add`: Nos permite subir un archivo desde el **directorio de trabajo** al **área de preparación** (index).
3. `git commit -m "mensaje"`: Subirá al **directorio de Git** (head) los archivos que se encuentran en el área de preparación (index), agregando un comentario para poder indentificarlo.
4. `git status`: Nos muestra el estado del **directorio de trabajo** y el **área de preparación** (qué cambios se han organizado, cuáles no y qué archivos están siendo rastreados por Git).
5. `git log`: Nos muestra una lista con todos los commits realizados con su respectiva información (mensaje).
6. `git checkout`: Con este comando podemos viajar a través de nuestros commits o ramas (más adelante veremos en detalle lo que son las ramas).
