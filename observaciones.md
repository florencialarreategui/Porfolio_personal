# Observaciones

Flor, felicitaciones por tu trabajo. Tu portfolio se ve muy lindo; es increible lo parecido que lograste que quedara al modelo de Ada y lo bien que armaste en general la estructura. 

El mayor problema en tu portfolio es que el responsive no funciona, lo que afecta negativamente tu nota a pesar de que se nota que pusiste esfuerzo. Seria una nota muchisimo mas alta si eso estuviera, pero una web sin responsive no está completa: la mayoría de nuestros usuarios van a ver nuestra web desde el celular, por lo que es absolutamente necesario poder ofrecerles la misma experiencia a ellos. Noto que tenés media queries, por lo que no sé si te faltó tiempo o no lo pudiste resolver. Si es el segundo caso, me escribirías? Asi podemos verlo juntas más en detalle.

Para resolver el formulario noto mucha, demasiada, dependencia del modelo de Ada, incluso en casos donde no tiene sentido con el codigo que ya tenes. El CSS esta calcado, te traes variables de css que usa Ada, un tema que nosotras no vimos y que no sirve de nada en tu codigo. Tenes clases y elementos que no te suman nada, como "form-control". No necesito decirte por qué esto no me impresiona, pero lo más grave es que te deja a vos sin aprender: no creo que hayas aprendido del todo como maquetar vos sola ese formulario, asi que mirar el modelo de Ada en ese caso no sólo no te suma para el TP sino que te roba la oportunidad de aprenderlo. Cuando tengas el tiempo, sin la presión de la entrega encima, te super animo a que trates de hacerlo de cero. 

Te dejo varios comentarios para mencionar cositas puntuales. Como comentamos en clase, este trabajo no se hace para que constates conocimientos, sino para que aprendas: en ese sentido, mi intencion es que estos comentarios te sirvan para aprender, mejorar tu codigo a futuro e ir apreciando mejor qué se espera de nosotras como desarrolladoras front end.

## Estructura correcta de documento HTML

Cumplido en general. 

Algo que me llama la atención es tu `head`, dado que allí tenés una indicacion de css que no hace nada en tu pagina: 

```html
    <link media="only screen and (max-width: 375px)">
 ```

Esa es una media query y deberia estar en CSS, no tiene nada que hacer en un `link` de html. 

El "title" de tu web quedó como Document, lo que no es correcto, deberías tener un titulo que refleje que este es tu portfolio personal. 

El lenguaje del documento está en inglés, te comento en la sección de accesibilidad por qué eso es importante.

Tres cosas que haces ocasionalmete en tu HTML:
- usar etiquetas `br` para separar las cosas
- usar la etiqueta `<strong>` para darle grosor al texto
- usar "width" y "height" en el html. 
No llegué a comentarlo en clase, pero esto es incorrecto. Esas etiquetas son un resabio de viejas épocas en las cuales css no era tan poderoso como ahora, pero usarlas hoy viola uno de los principios básicos de programación: la separación de responsabilidades. Los estilos se dan con css, la estructura se da con html. Una decisión de estilo como un espaciado entre dos elementos debe controlarse con css -flex, elementos en bloque, etc, no con `br`.

## Respeta la consigna

- El portfolio cuenta con las secciones solicitadas 

Cumplido

- Al clickear en los links de navegación, debe llevar a la sección correspondiente

Te faltó en el link "contacto" del footer. 

- Al clickear en los links de contacto, debe llevar a la página externa correspondiente 

Cumplido.

- El portfolio debe tener un diseño responsivo y verse correctamente en distintos dispositivos 

No cumplido. Tu pagina web se ve bien en dos soluciones nada mas: en escritorios grandes, y en celulares muy pequeños (de 375px para abajo: muchos celulares tienen 450px y hasta 575px). Esa es la unica media query que tenes, pero deberian ser muchas mas, para poder adaptarse a todos los dispositivos desde los que los usuarios pueden entrar a nuestra web. 

Creo que comenté en clase que lo más habitual es seguir las media queries que sugiere bootstrap. Te las dejo como una guia para futuros trabajos:

```css
/* Monitores grandes */
@media (max-width: 1400px) {
  ...;
}

/* Monitores pequeños */
@media (max-width: 1200px) {
  ...;
}

/* Tablets  */
@media (max-width: 992px) {
  ...;
}

/* Celulares en modo horizontal y tablets pequeñas */
@media (max-width: 768px) {
  ...;
}

/* Celulares: hasta 320px debería verse bien */
@media (max-width: 576px) {
  ...;
}
```

Para los celulares, veo además que el formulario tampoco es responsive a pesar de que intentaste. En tu media query decis:

```css
.section-formulario{
    display: flex;
    flex-direction: column;
}
```

Pero seccion-formulario tiene un solo descendiente, .div-formulario, asi que no afecta en nada esta orden. Quiza lo que querias era decirle a div-formulario que fuera flex y en dirección column. Si haces eso tu form se va a ver mucho mejor, pero todavia no va a ser totalmente responsive. Tenes muchisimos `padding` en los divs que componen tu formulario que tenes que eliminar en responsive, porque sino los textos no van a entrar comodamente en el poco espacio que tenemos en un celular. Como minimo deberias hacer mas pequeños los padding de .div-formulario y de .contactame.

Noto que para hacer las estructuras de las tarjetas usaste divisiones con divs, en lugar de hacer un solo div contenedor y acomodar las tarjetas con flex-wrap: wrap. Eso te va a traer *muchisimos* problemas para hacer la estructura de las tarjetas adaptable a tablet y escritorios pequeños. En la clase 21, alrededor de 1:40, hablamos de como hacer esta estructura con flex. Te recomiendo que la repases para empezar a encarar el responsive en las secciones de las tarjetas, que son las mas complejas. 

- El portfolio debe estar deployado y ser accesible desde una URL 

No cumplido, o al menos no tenes el link en el README, por lo que nadie puede acceder a tu portfolio. 

- El repositorio en GitHub debe tener un readme adecuado 

No cumplido. El readme es muy importante para que quienes vayan a tu github puedan conocer mas sobre tus proyectos. 

### Respeta el diseño dado 

Cumplido, pero hay detalles en donde te alejás del diseño. Es muy importante tratar de seguirlo lo más posible. 

Notá el espaciado de tu barra de navegación vs el modelo: tu botón de "contacto" está pegado al borde derecho de la página, mientras que en el modelo hay una distancia que hace que todo se vea mejor. Un `padding-right` en el `ul` podria ayudarte. 

Detalles asi abundan por tu proyecto: la distancia entre los titulos y los subtitulos, la distancia entre las distintas secciones, el alto de algunos elementos. Son detalles, pero mientras mas nos acerquemos al modelo, mejor. 

### Buena estructura de proyecto 

Cumplido. No entiendo por que hay un archivo llamado "correcciones.txt", si era un documento de trabajo para vos no debería estar en una entrega. Tambien nota que tenés una carpeta innecesaria, `vscode`, que es agregada a veces automáticamente por Visual Studio. Es buena práctica borrarla antes de una entrega. 

Si vas a tu consola vas a ver que tenes un error para la imagen `<img src="./images/icon-error.svg"> `. Eso es porque estas diciendo en el html que la carpeta se llama "images", cuando en realidad se llama "imagenes". Veo ademas que tenes algunas imagenes en la carpeta que no usas en tu codigo. 

### Código bien indentado 

No cumplido. Veo el intento, pero el identado está muy desprolijo y dificulta la lectura de tu codigo. 

Sé que es difícil entender la importancia a esta altura, pero la indentación adecuada es realmente importantísima para poder leer tu código. Muchas veces se hace absolutamente imposible saber qué está adentro de cada cosa, y leer tu HTML en particular es muy, muy difícil. Recordá que haciendo click derecho + "formatear documento" podés corregir rápidamente el tabulado, y esto también te va a ayudar a encontrar rápidamente errores como etiquetas mal cerradas. 

Cada vez que una etiqueta esta adentro de otra, debemos dejar dos o cuatro espacios (eso va a preferencia de cada una). Visual Studio Code va a tratar de ayudarte en eso. Por favor, prestale atención para la próxima vez. 

En tu caso veo que usas cuatro espacios. Cada vez que una etiqueta se abre, sus descendientes deben tener cuatro espacios de sangria:

```html 
<body>
    <header>
        <ul>
            <a href="#hola"> <li class="lista1">HOLA</li></a>
            <a href="#conocimientos"> <li class="lista1">CONOCIMIENTOS</li></a> 
            <a href="#proyectos"> <li class="lista1">PROYECTOS</li></a>
            <a href="#contacto"> <li class=" lista1 boton">CONTACTO</li></a> 
        </ul>  
    </header>
```

En tu caso a veces dejas 8, a veces 4, a veces ninguno. 

No esta mal, si el codigo es cortito, dejar dos etiquetas en la misma linea, como hiciste en tus `a` y `li` en el ejemplo de arriba. Pero cuando se hace tan largo que hay que hacer un scroll horizontal para leer el codigo, es absolutamente necesario que dejes salto de linea entre etiquetas. Esta linea es imposible de leer:

```html
<a href="#hola"> <div class="div-proyectos"><img src="https://frontend-proyecto-portfolio.adaitw.org/images/Screen%20Shot%202020-07-12%20at%2014.31.06.png" alt="" width="276px" height="218px"> <br><h3 class="nombre-proyectos">Porfolio</h3></div></a>```

Deberia ser:

```html
<a href="#hola">
    <div class="div-proyectos">
        <img src="https://frontend-proyecto-portfolio.adaitw.org/images/Screen%20Shot%202020-07-12%20at%2014.31.06.png" alt="" width="276px" height="218px">
        <br>
        <h3 class="nombre-proyectos">Porfolio</h3>
    </div>
</a>
```

Lo mismo ocurre en el css. En CSS el identado se deja, por ahora, sólo para las media queries. A veces ademas del tabulado, no dejas el espaciado correcto en cada orden. En lugar de escribir por ejemplo `.name{`, deja un espacio entre el nombre de la clase y la llave: `.name {`

### Comentarios que permiten mejorar la legibilidad del código 

Cumplido, pero tu CSS esta desprolijo (tenes por ejemplo dos secciones de mis conocimientos). Eso te ocasiona errores a vos misma: hay incluso codigo que esta repetido!

Ordená tu CSS, que lo que esta primero en HTML esté también primero en CSS. Si tu orden sigue el de HTML vas a ver que se hace todo muchisimo mas facil. Y tambien vas a encontrar algunos estilos que tenes repetidos y que te van a dificultar corregir tu codigo. 

### Uso correcto de etiquetas semánticas 

Muchos problemas acá. 

Usás `header` para la barra de navegación, eso debería sí o sí ser un nav (un lector de pantalla va a buscar el nav para darle opciones de navegación al usuario). Si bien en algunos diseños identificar el `header` es complejo, creo que en este caso definitivamente debe incluir a la primera sección "portada". Un `header` representa siempre lo que llamamos "contenido introductorio": todo aquello que da la bienvenida a nuestra web, sin dar información más específica (pero invitándonos a verla)

Creo también que las tarjetas de producto deberían ser `article` en lugar de `div`. Esto permite que los usuarios de lectores de pantalla los encuentren fácilmente, y también ayuda al SEO. Todo elemento que sea autocontenido, reusable, repetible y pueda usarse en diferentes contextos, debe ser un article. Sobre ese tema te dejo una lectura: https://www.smashingmagazine.com/2020/01/html5-article-section/

Uno de tus titulos de seccion es un h3, a pesar de que tiene la clase h2. El h1 es el titulo principal, y debería haber sólo uno por página. El resto deberían estar en orden de jerarquía: h2 para los titulos de secciones, h3 para los títulos dentro de cada subsección, etc. En este caso, "Mis conocimientos", "Mis proyectos" etc deberían ser h2 y los títulos de las cards deberían ser h3. 

### Buenos nombres de clases 

Cuando decimos que un nombre de clase debe ser descriptivo, lo decimos en un sentido funcional: qué rol cumple este elemento en el código. Los colores de los elementos, su forma, su estilo, su posición, todas esas cosas pueden cambiar y efectivamente cambian todo el tiempo en las webs que hacemos. El botón que hoy es un circulo mañana será cuadrado; la sección que estaba primera mañana estará tercera, por lo que no sirve decir "lista2". Esos factores no son buenos descriptores, y no deberían ser parte de nuestros nombres de clases. "lista2" contiene los links de navegacion del footer: que acompaña la seccion cita: "links-navegacion-footer" es mas claro. 

Ocasionalmente usas etiquetas de html como nombres de clase (div-formulario por ejemplo). Los nombres de clase describen funcionalidades, no codigo. Qué hace ese div en tu pagina? Que funcion cumple? Si ayuda a los estilos del form, en el sentido de que da los bordes, espaciado, etc, entonces "decoracion-formulario" es mas correcta. 

En resumen, a la hora de darle un nombre de clase a algo, pensá qué es ese elemento, qué función cumple en tu página. 

### Código CSS bien estructurado 

Noto muchos estilos innecesarios o confusos, que te voy indicando en tu archivo de css. Muchisimo desorden, codigo comentado, y ordenes repetidas. Vale la pena recorrer este CSS de nuevo y mejorarlo.  

### Reutilización de estilos 

Cumplido en general. 

### Cumple con criterios básicos de accesibilidad 

El lenguaje de tu documento de HTML está en inglés, por lo que un lector de pantalla va a tratar de leer todos tus textos en inglés. El efecto es muy feo y confuso: pronuncian en inglés las palabras en español, así que si ven "generador de memes" van a leer "yiniradour di mims". Siempre tratá de que el atributo `lang` de tu HTML refleje el idioma de los textos en tu página.


Eliminas el outline en tu formulario. No puedo insistir lo suficiente en esto: **nunca** se elimina el outline de los elementos a menos que tengas una alternativa bien testeada que funcione bien en todos. Tu pagina es imposible de recorrer con teclado: la mitad de las veces no hay forma de saber en donde estamos paradas. 

Te faltan muchas etiquetas semanticas como te comenté en esa sección que harían que tu web sea mas amable con el lector de pantalla. 

- Los colores tienen un contraste adecuado 

Cumplido. 

- Las imágenes tiene el atributo `alt` que corresponde 

No cumplido. Solo la imagen principal y las de tecnologia tienen alt, el resto estan vacios. 

Las imágenes le comunican muchisimas cosas a tus usuarios videntes. No es casualidad que para tu portada hayas elegido una mujer con una computadora: este es tu portfolio despues de todo, y queres transmitir rapidamente "este es el sitio de una mujer programadora". Si hubieras elegido la imagen de un hombre haciendo malabares la primera impresión de tu sitio sería muy distinta. Esa misma información, tenemos la obligación de transmitirsela a quien no puede ver tus imagenes. "Mujer programadora junto a una computadora" es una descripción más clara y mejor que "Ada", que no le dice nada al usuario. 

El alt es un texto que lee el lector de pantalla, por lo que no debés usar guiones como en "react-logo". 

Hay ocasiones en las cuales agregar un alt, paradojicamente arruina la experiencia. Considerá tus tarjetas de tecnologias. El lector va a leer:

"Sección: Mis conocimientos. Imagen: html5. Texto html 5. Imagen: css. Texto: css"... y asi. Si la idea es que el usuario no vidente conozca las tecnologías que manejas, esto es repetitivo y molesto. En estos casos podemos agregar "aria-hidden" a la imagen, ya que no suma nada. 

Tus `links` tambien necesitan un aria asi el usuario sabe adonde va a ir. Si falta, el lector de pantalla lee la url, lo cual es muy molesto. Algo asi es mucho mejor: `<a href="https://twitter.com/JuannaDeArco aria-label="Mi twitter">`


- Los íconos y elementos que no presentan texto agregan la información correspondiente por otros medios (etiquetas aria, texto oculto) 

No cumplido. 

- Los íconos y elementos que no necesitan ser anunciados por un lector de pantalla tienen la etiqueta aria
correspondiente 

No cumplido. Te super animo a que repases la clase de accesibilidad si necesitas ver esto. 

- Commits con mensajes adecuados 

Tenes relativamente pocos commits, tomalo en cuenta para futuros trabajos. 

- Cuenta con un favicon

No cumplido. 

### Nota: 7