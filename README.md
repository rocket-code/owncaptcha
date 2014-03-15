OwnCaptcha
==========

Simple Captcha para PHP


Versión
-------

- __1.0.0__

Licencia
-------

[MIT License](http://www.opensource.org/licenses/mit-license.php)

Instalación
-----------

### Requerimientos

- PHP 5.3.*

### Github

    cd /var/www
    git clone git@github.com:mostofreddy/owncaptcha.git
    cd owncaptcha
    composer install

### Composer

    "require": {
        "php": ">=5.3.0",
        "mostofreddy/owncaptcha": "*",
    }

Roadmap & issues
----------------

[Roadmap & issues](https://github.com/mostofreddy/owncaptcha/issues)

Changelog
---------

__1.0.0__

* Release

Features
========

* Tiempo de vida de un captcha
* Guarda en session el codigo del captcha para su posterior recuperación
* Genera la imagen del captcha de forma automática
* Sanado automatico de los valores de session y provenientes del formulario
* Fácil de extender con nuevos Adapters para implementar distintos tipos de Captchas

Docs
====

Captcha
-------

### Tiempo de vida del captcha

El tiempo de vida del captcha se configura mediante el método ttl.
*Default: 60 seg*

    $captcha = new \owncaptcha\Catpcha();
    $captcha->ttl(3600); //1 hora

### Sessiones

__Habilitar/deshabilitar sessiones__

Para habilitar/deshabilitar que el script guarde el valor del captcha en sessiones:
*Default: true*

    $captcha->sessionSave(true); //o false

__Variable donde se almacena el valor del capcha en session__

Con el método setSessionVar se puede cambiar la variable donde se almacena el captcha en session
*Default: owncaptcha*

    $captcha->setSessionVar('myvar');

### Validación

La validación se realiza con el método validate

    $code = (isset($_POST['code']))?$_POST['code']:'';
    $result = $captcha->validate($code); // true or false

Apdaters
--------

Los adapters son distintas clases que implementan la lógica de como renderizar el captcha.

Solo hay uno disponible.

### TextImage

Este adapter crea una imagen con un texto aleatorio.

#### Configuración

    $adapter = new \owncaptcha\adapters\TextImage();
    $adapter->config(
        array(....)
    );

* __width__: (int) ancho de la imagen
* __height__: (int) alto de la imagen
* __bg__: (array) color de fondo (rgb)
* __forecolor__: (array) color del testo (rgb)
* __linecolor__: (array) color de las lineas del fondo (rgb)
* __lines__: (int) cantidad de lineas en el fondo
* __enablettf__: (bool) indica si se usa una tipografia ttf o del sistema (true: usa ttf, false: usa del sistema)
* __ttf__: (string) ubicación de la fuente ttf
* __fontsize__: (int) tamaño de la fuente ttf
* __padding__: (int) padding de la imagen
* __lineweight__: (int) grosor de las lineas de fondo