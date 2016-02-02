## Buenas Prácticas CSS

### 1. Que sea legible.
La legibilidad de tu CSS es muy importante ya que hace que sea mantenible en el futuro además de que podrás encontrar
los elementos más rápido. Ten en mente alguien más podrá modificar tu código en un futuro.

**Grupo 1: Todo en una línea**
```css
.button { background-color: grey; border: 1px solid black; font-size: 13px; }
```

**Grupo 2: Cada estilo en una línea**
```css
.button {
    background-color: grey;
    border: 1px solid black;
    font-size: 13px;
}
```

Las dos prácticas son aceptables aunque por lo general ocupamos el segundo grupo para bloques con más de 3 estilos.
Elige el método que se vea mejor.


### 2. No reinventes la rueda.
Crea estilos independientes que puedan ser reutilizados en todo el proyecto o mejor aún en la mayoría de los proyectos.
Por ejemplo yo uso el estilo “align-middle” para la alineación vertical en relación a objetos hermanos.

```css
.align-middle{
    display: inline-block;
	vertical-align: middle;
}
```

Ya que el estilo cumple con una tarea específica lo puedo ocupar en diferentes elementos sin afectar las propiedades
que lo definen.


### 3. Resetea los estilos
Recuerda que los sitios que desarrollamos se va a abrir en diferentes navegadores, lamentablemente cada navegador tiene
estilos default para muchos elementos, por ejemplo un título puede tener un margen mayor en FireFox que en
Internet Explorer. Puedes ocupar [normalize](https://necolas.github.io/normalize.css/) o resetear los estilos
manualmente para que los navegadores respeten los estilos del título.


### 4. Utiliza la estructura top-down
Recomiendo utilizar el formato top-down ya que los estilos aparecerán en relación a cómo aparecen los elementos en tu
sitio web, esto ayudará a que tus estilos tengan una secuencia y puedas ubicarlos más rápido. Por ejemplo para un sitio
 con esta estructura:

```html
<section id=”about-us”></section>
<section id=”products”></section>
<section id=”contact”></section>
```

Los estilos aparecerán así:

```css
#about-us { ... }
#products { ... }
#contact { ... }
```


### 5. Combina elementos
Es común que en un sitio existan elementos que comparten propiedades, en lugar de volver a escribir el estilo
¿por qué no combinarlos?. Por ejemplo los títulos h1, h2 y h3 podrían compartir el mismo color y la misma fuente

```html
h1,
h2,
h3 {
    font-family: ‘Arial’, sans-serif;
    color: #333;
}
```

Después podrías agregar características únicas como el tamaño de fuente.


### 6. Primero crea tu HTML (Maquetación)
Muchos programadores escriben su CSS al mismo tiempo que escriben el código HTML, aunque desde mi punto de vista
podrías ahorrar más tiempo si creas la maqueta HTML primero. La razón es que tener el HTML te permite visualizar toda
la página y los elementos que lo componen, después solo tienes que encargarte de darle vida. Recuerda la estructura
top-down para no perderte.


### 7. Utiliza múltiples clases
Utilizar múltiples clases en un elemento resulta de beneficioso. Imagina que tienes un elemento “div” que representa
una caja que quieres hacer flotar a la derecha y tienes una clase .right que hace flotar todo a la derecha,
simplemente tienes que agregar el nombre de la clase en el elemento de la siguiente manera:

```html
<div class=”box right”></div>
```

Puedes seguir agregando más clases en un elemento. Como ya lo había mencionado, tener clases que realicen una tarea
independiente te ahorrará código al final.

Usé como ejemplo una caja alineada a la derecha pero recuerda seguir el flujo de los elementos en un sitio web, si
tienes que modificar el flujo de los elementos usando CSS probablemente tu maquetació esté mal ya que esto no es
semántico. Recuerda

> _El HTML es para la estructura y contenido y el CSS es para su presentación._


### 8. Comenta tu CSS
Al igual que otro lenguaje, es muy buena idea comentar tu código por secciones o por objeto.


### 9. Ordena tu CSS de manera alfabética
Ordenar tus estilos de manera alfabética te ayudará a ubicar una regla dando una escaneada rápida a un estilo. Por
otra parte también mejorará la legibilidad de tu código.


### 10. Minimiza tu código CSS
Cuando tu sitio web está listo para producción es muy recomendable minimizar el código CSS ya que eliminará saltos de
línea, espacios en blanco etc. Esto reducirá considerablemente el tamaño del archivo lo que acelerará la carga en el
navegador además de que los buscadores darán una mejor calificación para lograr un SEO orgánico.


### 11. Usa “margin: 0 auto” para centrar layouts
Estoy seguro que hay muchas formas de alinear bloques al centro de la página pero no te compliques calculando medidas
o forzando un elemento a tener propiedades que no le corresponden.


### 12. No todo necesita estar envuelto en un div
Antes de envolver un elemento en un div y asignarle una clase con sus respectivos estilos analiza si se puede agregar
los estilos directamente al elemento por ejemplo

```html
<div class=”header-text”><h1>Header Text</h1></div>
```

Sería más fácil agregar los estilos directamente al título

```html
<h1>Header Text</h1>
```

Aunque recuerda que todo depende de cómo hagas la estructura de tu HTML.


### 13. Usa herramientas para desarrollador
Si no tienes una herramienta para desarrollador como Chrome DevTools o Firebug detén los que estás haciendo y empieza
a usarla. Entre las diferentes características de estas herramientas puedes inspeccionar, modificar y editar CSS en
tiempo real, algo que seguramente te ahorrará muchos “refresh” de la página que estás desarrollando.


### 14. Intenta evitar el uso de la posición absoluta
El posicionamiento absoluto es muy útil cuando tienes que posicionar un elemento en el pixel exacto, sin embargo si el
elemento tiene que convivir con más elementos este no los respetará y podría darte dolores de cabeza al intentarlos
alinear manualmente.


### 15. Utiliza text-transform
La propiedad text-transform es muy útil ya que te permite estandarizar la forma en que se formatea el texto de tu
sitio. Supón que estás queriendo crear títulos que sólo tienen letras minúsculas a mayúsculas pero sólo en el diseño
de tu página y para los resultados del navegador quieres mostrarlos de una forma capitalizada, solo tendrías que
añadir la propiedad text-transform de la siguiente manera:

```css
.text-uppercase {
	text-transform: uppercase;
}
```


### 16. No utilices márgenes negativos para ocultar elementos
Muchas veces queremos ocultar el texto del logotipo de la página usando CSS con las propiedades
_display: none_, _text-indent: -9999em_ o usando márgenes negativos y antes estaba bien hasta que Google lo empezó a
detectar como posible spam. En estos casos intenta utiliza el atributo alt de la imagen.


### 17. Em’s vs Pixeles
Siempre ha habido un debate entre si es mejor usar píxeles o ems para definir el tamaño de fuente. Los pixeles es una
forma estática de definir el tamaño de fuente mientras que los ems son más escalables en diferentes tamaños de
navegadores y dispositivos móviles. Actualmente con el uso de diferentes tipos de navegador los ems se han vuelto más
populares para los tamaños de fuente si te interesa podrías leer este artículo [differences betweetn the measurement
sizes](http://webdesign.about.com/cs/typemeasurements/a/aa042803a.htm).


### 18. No subestimes a las listas
Las listas son una muy buena forma de presentar datos estructurados y su formato es fácil de manipular con CSS. Las
listas también son muy útiles a la hora de crear menús de navegación, te podrías ahorrar muchos divs.


### 19. Evita selectores extras
Si pensamos en los elementos de una página como objetos o componentes independientes no tendrás que ser muy específico
a la hora de declarar los estilos para no sobreescribir otros. Imagina este ejemplo

```html
body #container .main-nav {
	...
}
```

Cuando fácilmente podrías utilizar un solo selector

```html
.main-nav {
	...
}
```


### 20. Usa múltiples hojas de estilo
Mientras estás desarrollando el sitio puedes crear un estilo para cada objeto o componente con el fin de mantener más
independientes los trozos de código y hacerlo más legible. Solo recuerda que cuando tengas que llevar el sitio a
producción es mejor para la velocidad de la página tener solo un archivo de estilos y minimizado.
