---
layout: post
title:  "Todo lo que necesitas saber sobre Git y Github"
date:   2021-04-12 22:03:46
---

## ¿Qué es Git?

Git corresponde a un **sistema de control de versiones** desarrollado por Linus Torvalds.

No olvidemos que cuando hablamos de **control de versiones**, nos referimos a la gestión de los diversos cambios que se realizan sobre un proyecto (subir código a la nube, añadir alguna parte o simplemente editar algo que no funciona correctamente, entre otros).

Por lo tanto, un sistema de control de versiones serían todas las herramientas que nos permiten hacer esas modificaciones antes mencionadas sobre nuestro trabajo, haciendo más fácil la administración de las distintas versiones.

## Git en el mundo

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

## Instalación y configuración de Git

En Sistemas Operativos como Ubuntu o Mac OS Git ya viene instalado, por lo que solo debemos configurarlo. Para ello abrimos la terminal y tecleamos lo siguiente:

{% highlight r %}
$ git config --global user.name "YOUR NAME"
$ git config --global user.email "YOUR@EMAIL.com"
{% endhighlight %}

En **YOUR NAME** debe ir nuestro nombre y en **YOUR@EMAIL.COM** el correo que utilizamos o utilizaremos para nuestra cuenta de Github.

## Flujo de trabajo

Git está compuesto por tres estados o árboles en los que se pueden encontrar los archivos de nuestro proyecto:

1. **Working directory**: Directorio de Trabajo, contiene nuestro archivo o conjunto de archivos del proyecto.
2. **Staging area**: Área de Preparación, también es conocida como **index** y actúa como una zona intermedia en donde escogeremos qué archivos están listos para pasar al siguiente estado y/o cuales no lo están por el momento.
3. **Git directory**: Directorio de Git, también se le conoce como **head** y corresponde al repositorio donde se encuentra el registro de todo nuestro proyecto (commits).

<img src="{{ site.baseurl }}/assets/img/EstadosGit1.jpg">

Aquí es donde aparece una nueva palabra: **commit**. Un commit corresponde a la acción de guardar o subir un archivo o conjunto de archivos al Directorio de Git (head).

## Primeros commits y viajes en el tiempo

### `git init`

Se utiliza para inicializar un repositorio local.

{% highlight r %}
$ git init
{% endhighlight %}

### `git add`

Nos permite subir un archivo desde el **directorio de trabajo** al **área de preparación** (index).

{% highlight r %}
$ git add index.html
{% endhighlight %}

Si queremos subir todos los archivos del directorio de trabajo, utilizamos `-A`:

{% highlight r %}
$ git add -A
{% endhighlight %}

Para devolver al directorio de trabajo un archivo que se encuentra en el área intermedia, utilizamos `rm --cached`:

{% highlight r %}
$ git rm --cached index.html
{% endhighlight %}

### `git commit -m "mensaje"`

Subirá al **directorio de Git** (head) los archivos que se encuentran en el área de preparación (index), agregando un comentario para poder indentificarlo.

{% highlight r %}
$ git commit -m "Primer commit"
{% endhighlight %}

### `git status`

Nos muestra el estado del **directorio de trabajo** y el **área de preparación** (qué cambios se han organizado, cuáles no y qué archivos están siendo rastreados por Git).

{% highlight r %}
$ git status
{% endhighlight %}

### `git log`

Nos muestra una lista con todos los commits realizados con su respectiva información (mensaje).

{% highlight r %}
$ git log
commit 7fd525835c8c0359ea13fd982a04251d61832ab6 (HEAD -> master)
Author: YOUR NAME <YOUR@EMAIL.COM>
Date:   Sat Apr 25 21:22:20 2020 -0400

    Segundo commit
    
commit 7827ceb120fbc23a8bc18e1e9c680ce1f731fed2
Author: YOUR NAME <YOUR@EMAIL.COM>
Date:   Mon Apr 20 18:58:58 2020 -0400

    Primer commit
{% endhighlight %}

### `git checkout`

Con este comando podemos viajar a través de nuestros commits o ramas (más adelante veremos en detalle lo que son las ramas).

{% highlight r %}
$ git checkout 7fd525835c8c0359ea13fd982a04251d61832ab6
{% endhighlight %}

Si queremos regresar al último commit, utilizamos `master`:

{% highlight r %}
$ git checkout master
{% endhighlight %}

**Importante**: `master` siempre corresponderá al último commit que nosotros hayamos generado, mientras que el `head` podrá variar dependiendo de lo que le indiquemos por medio del comando `checkout`.

## Reset

El comando `reset` funciona de manera similar a `checkout`, con la diferencia de que este elimina los commits a su paso. Existen 3 niveles o tipos de borrado:

### `reset --soft`

Este tipo de reset nos permite viajar a un commit en específico, borrando los posteriores a este. Sin embargo, mantiene nuestro directorio de trabajo intacto.

{% highlight r %}
$ git reset --soft 7827ceb120fbc23a8bc18e1e9c680ce1f731fed2
{% endhighlight %}

### `reset --mixed`

Funciona de manera similar al anterior (soft), borrando también los archivos que se encuentren en el área de preparación (index). Tampoco se involucra con nuestro directorio de trabajo.

{% highlight r %}
$ git reset --mixed 7827ceb120fbc23a8bc18e1e9c680ce1f731fed2
{% endhighlight %}

### `reset --hard`

Como su nombre lo indica, borra absolutamente todo lo que hay después del commit al que queremos viajar, afectando incluso nuestro directorio de trabajo.

{% highlight r %}
$ git reset --hard 7827ceb120fbc23a8bc18e1e9c680ce1f731fed2
{% endhighlight %}

## Ramas y fusiones

Una rama en Git vendría siendo una especie de línea de tiempo de un proyecto, la cual se construye mediante nuestros commits.

Cuando nosotros inicializamos nuestro repositorio local con el comando `git init`, Git internamente genera la rama principal o **rama master**, es decir, la línea de tiempo por defecto en la que estaremos trabajando.

Las ramas son utilizadas por lo general para desarrollar funcionalidades aisladas unas de otras (como el testing, por ejemplo).

### Ramas

Crear una nueva rama en Git es bastante sencillo:

{% highlight r %}
$ git branch testing
{% endhighlight %}

Ten en cuenta que al momento de crear una nueva rama, ésta contará con los **mismos commits** que la rama master.

El comando `git branch` a secas nos permite listar todas las ramas existentes, marcando con un asterisco en la que estemos actualmente:

{% highlight r %}
$ git branch
* master
  testing
{% endhighlight %}

Si tienes buena memoria, recordarás que `checkout` nos permite viajar entre commits y ramas, por lo que si queremos cambiarnos a la rama testing, debemos hacer lo siguiente:

{% highlight r %}
$ git checkout testing
{% endhighlight %}

Por lo tanto, si ejecutamos el comando `git branch`, el asterisco debería estar sobre esta nueva rama:

{% highlight r %}
$ git branch
  master
* testing
{% endhighlight %}

Si por alguna razón queremos borrar la rama que hemos creado (porque ya no nos sirve o simplemente porque los cambios en esta línea de tiempo contienen muchos errores), debemos posicionarnos primeramente en la rama principal y ejecutar lo siguiente:

{% highlight r %}
$ git branch -D testing
{% endhighlight %}

### Fusiones

Una fusión en Git consiste en la unión de dos ramas, proceso que consta de 2 pasos muy importantes:

1. Situarnos en la rama que va a absorver a la otra.
2. Ejecutar la fusión.

Si tomamos el ejemplo anterior, fusionaremos la rama master con testing, siguiendo los pasos respectivos:

{% highlight r %}
$ git checkout master
$ git merge testing
{% endhighlight %}

Al hacer un `git log` nos podremos dar cuenta que la rama master también cuenta con los commits de la rama que acabamos de absorver.

## Github

Github corresponde a un sitio que nos permite contar con las virtudes de Git como sistema de control de versiones pero en Internet, dándonos ciertas ventajas como compartir nuestro trabajo y/o trabajar con más personas.

Tanto Github como otros sitios que cumplen la misma función (Gitlab o Bitbucket, por ejemplo) se han convertido hoy en día en redes sociales para los programadores ya que como se especificó anteriormente, nos permiten compartir nuestro trabajo (muchas empresas revisan nuestros perfiles de Github para tener conocimiento de nuestros trabajos realizados) y trabajar con más personas (por ejemplo, un equipo de desarrolladores de software).

Es importante considerar que Github se suma al flujo de trabajo de Git como un cuarto estado o árbol:

<img src="{{ site.baseurl }}/assets/img/EstadosGit2.jpg">

### Registro y configuración de la llave SSH

Hola amigos.
