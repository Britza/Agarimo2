# Página web Agarimo

### Creación tema hijo:

Para crear un tema hijo en wordpress primero tenemos que crear la carpeta child del tema elejido por nosotros, en nuestro caso es el tema fluida.
Para crear la carpeta, desde pHpStorm nos dirijimos a la siguiente ruta **wordpress/wp-content/themes/** y dentro creamos la carpeta con el nombre de nuestro
tema y -child , fluida-child.
Para que el tema hijo funcione necesita un style.css y un archivo functions.php, por lo que deberemos crear estos archivos.

Primero creamos la hoja de estilo style.css y le añadimos el siguiente comentario:
```
/*
 Nombre del tema:	[Nombre del tema padre] Child
 URI del tema:	[http://example.de/parent-theme/]
 Descripción:	[Nombre del tema padre] Tema hijo
 Autor:	[Tu nombre]
 URI del autor:	[El URL de tu sitio web]
 Plantilla:	[Nombre de la carpeta del tema padre] 
 Versión:	1.0.0
Dominio de texto:	[Nombre del tema padre] -child
*/
```
 Luego desde el style.css ya puedes modificar el estilo del tema.
 En nuestro caso cambiamos el estilo de la letra del titulo de las entradas:
 ```
 .entry-title{
    color: #0085b2;
}
```
Esto queda así : 

![imagen titulo](https://github.com/Britza/Agarimo2/blob/master/html/wp-content/themes/fluida-child/imagenes/fluida-child6.png)  

también le cambiamos el color a la etiqueta buscar para hacerla más visible así como a los bloques interiores

```
.wp-block-searchlabel{
    color:#8224e3;
}
.wp-block-groupinner-container{
    color:black;
}
```
![imagen color](https://github.com/Britza/Agarimo2/blob/master/html/wp-content/themes/fluida-child/imagenes/fluida-child7.png)  

Una vez creado el css se deberá programar funcitions.php
Este archivo determina el orden en el que se cargan las hojas de estilo de los temas padre e hijo de WordPress.
Para que los cambios del tema hijo anulen las instrucciones del tema padre, el navegador debe cargar la hoja de estilo del tema hijo de WordPress después de la hoja de estilo del tema padre.
En este archivo pondremos lo siguiente.
```
<?php
add_action( 'wp_enqueue_scripts', 'my_theme_enqueue_styles' );
function my_theme_enqueue_styles() {
    $parenthandle = 'parent-style'; // This is 'fluida-style' for the Twenty Fifteen theme.
    $theme = wp_get_theme();
    wp_enqueue_style( $parenthandle, get_template_directory_uri() . '/style.css',
        array(),  // if the parent theme code has a dependency, copy it to here
        $theme->parent()->get('Version')
    );
    wp_enqueue_style( 'child-style', get_stylesheet_uri(),
        array( $parenthandle ),
        $theme->get('Version') // this only works if you have Version in the style header
    );
}
```

Una vez creado estos dos archivos ya podremos activar en nuestro wordpress el tema hijo. Esto se hace  como cualquier otro tema en el backend de WordPress,se entra en el backend y selecciona el tema hijo en Diseño > Temas.

### Backend

Para modificar nuestro tema desde el backend de wordpress solo tenemos que ir a el tema elegio y darle a personalizar. Dónde aparecerá el siguiente menú:

![menu](https://github.com/Britza/Agarimo2/blob/master/html/wp-content/themes/fluida-child/imagenes/fluida-child8.png)  

### Nuestro tema:

Inicio  
![fluida-child1](https://github.com/Britza/Agarimo2/blob/master/html/wp-content/themes/fluida-child/imagenes/fluida-child.png)  

Quienes somos
![fluida-child2](https://github.com/Britza/Agarimo2/blob/master/html/wp-content/themes/fluida-child/imagenes/fluida-child2.png)  

Contacta con nosotros
![fluida-child3](https://github.com/Britza/Agarimo2/blob/master/html/wp-content/themes/fluida-child/imagenes/fluida-child4.png)  

Condiciones de los servicios
![fluida-child4](https://github.com/Britza/Agarimo2/blob/master/html/wp-content/themes/fluida-child/imagenes/fluida-child5.png)  

Comentarios
![comentarios](https://github.com/Britza/Agarimo2/blob/master/html/wp-content/themes/fluida-child/imagenes/fluida-child3.png)  

