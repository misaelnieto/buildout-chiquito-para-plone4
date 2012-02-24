Buildout chiquito para Plone 4
==============================

Este es un buildout chiquito para que puedas instalar Plone 4 en modo 
desarrollo y en modo producción, pero sin tanto rollo o complicación.

Usa este buildout como base para tu proyecto si es que aun no estas 
muy acostumbrado a esto del buildout, pero quieres aprender o quieres
montar tu sitio en plone lo más rápido posible.

Instrucciones para obtener tu copia
===================================

.. note :: Lo siento, pero no tengo windows y tiene años que no lo uso.
   Así que no te podría dar mucha ayuda acerca de cómo usar ésto en 
   windows. *Sorry*.

Primero prepara tu sistema para que pueda compilar y ejecutar un 
montón de cosas.

Instala paquetes de desarrollo
------------------------------

Si estas en Ubuntu intenta ejecutar el siguiente comando como root o con
``sudo`` para instalar paquetes de desarrollo y compiladores::

  sudo apt-get install python-dev build-essential libpcre3-dev zlib1g-dev libjpeg62-dev libpng12-dev libncurses5-dev libxslt1-dev git python-pip libsasl2-dev pkg-config

La lista de paquetes cambia un poco para Debian 6::

  apt-get install python-dev build-essential libpcre3-dev zlib1g-dev libjpeg62-dev libpng12-dev libncurses5-dev libxslt1-dev git python-pip libsasl2-dev pkg-config

Para Fedora 15-16 y las AMI de Amazon usa yum::

  yum install nstall -y git make automake gcc gcc-c++ python-devel zlib-devel libxslt-devel openssl-devel pcre-devel ncurses-devel python-pip


Baja una copia de github
-------------------------

Clona el repositorio::

  git clone git://github.com/tzicatl/buildout-chiquito-para-plone4.git

Entra en el directorio::

  cd git://github.com/tzicatl/buildout-chiquito-para-plone4.git


Ejecuta ``bootstrap.py``
------------------------

El script bootstrap.y ayuda a generar directorios y archivos que van a ser 
necesarios para que buildout se ejecute correctamente::

  python -S bootstrap.py -c base.cfg

Ejecuta buidlout en modo desarrollo
-----------------------------------

El modo desarrollo instala varias herramientas de desarrollo junto con Plone::

  bin/buildout -c development.cfg

Pero te advierto. Tarda un montón en bajar todas las chunches.

Después de que termine, ya puedes arrancar plone así::

  bin/instance fg

Ejecuta buildout en modo producción
-----------------------------------

El modo proucción está diseñado para levantar un sitio Plone pequeño con 
relativamente poca carga. Pero bastará para la gran mayoría de los casos de uso.

Instalará una una instancia de plone configurada para acceder a un servidor ZEO. 
Además instalará otra instancia que se puede iniciar para dar acceso temporal al 
sitio además de la instancia principal.

Configura varnish y genera los archivos de configuración de VirtualHost para apache
y nginx.

Ya por último, instala supervisord para controlar los diferentes servicios desde un
solo punto.


