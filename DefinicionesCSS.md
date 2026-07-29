# Biblioteca de conceptos CSS

Esta biblioteca reúne definiciones, ejemplos y relaciones entre los conceptos de CSS estudiados. Los temas están organizados desde los fundamentos hasta propiedades de texto, unidades, fondos y posicionamiento.

## Índice

* [Selector de clase](#selector-de-clase)
* [Colores](#colores)
* [Texto](#texto)
* [Propiedades de texto](#propiedades-de-texto)
* [Fuentes web y variantes](#fuentes-web-y-variantes)
* [Unidades de medida en CSS](#unidades-de-medida-en-css)
* [Modelo de caja](#modelo-de-caja)
* [Ancho y alto](#ancho-y-alto)
* [Padding](#padding)
* [Bordes](#bordes)
* [Margin](#margin)
* [Centrado con `margin: auto`](#centrado-con-margin-auto)
* [Colapso de márgenes](#colapso-de-márgenes)
* [`box-sizing`](#box-sizing)
* [Tipos de caja](#tipos-de-caja)
* [Fondos](#fondos)
* [Posicionamiento en CSS](#posicionamiento-en-css)
* [Sobrescritura de propiedades](#sobrescritura-de-propiedades)
* [Selector universal y reset](#selector-universal-y-reset)
* [Ejemplo práctico: modelo de caja y tipos de caja](#ejemplo-práctico-modelo-de-caja-y-tipos-de-caja)
* [Ejemplo práctico: colores y fondos](#ejemplo-práctico-colores-y-fondos)
* [Ejemplo práctico: unidades de medida](#ejemplo-práctico-unidades-de-medida)
* [Ejemplo práctico: posicionamiento](#ejemplo-práctico-posicionamiento)

---

# Selector de clase

Una clase permite aplicar estilos a uno o varios elementos HTML.

En CSS se selecciona escribiendo un punto `.` seguido del nombre:

```css
.caja {
    background-color: teal;
}
```

En HTML se asigna mediante el atributo `class`:

```html
<div class="caja"></div>
```

La misma clase puede reutilizarse:

```html
<div class="caja"></div>
<section class="caja"></section>
<p class="caja"></p>
```

Todos esos elementos recibirán los estilos definidos en `.caja`.

---

# Colores

## `background-color`

Define el color de fondo de un elemento.

```css
.caja {
    background-color: teal;
}
```

## `color`

Define el color del texto.

```css
.caja {
    color: white;
}
```

## Formas de escribir colores

CSS permite representar colores mediante:

```css
color: darkslateblue;
color: rgb(242, 102, 222);
color: #ff0000;
color: hsl(200, 100%, 50%);
```

### Nombre

CSS incluye nombres de colores predefinidos.

```css
color: darkslateblue;
background-color: antiquewhite;
```

Son fáciles de leer, aunque ofrecen menos precisión que otros formatos.

### Hexadecimal

Los colores hexadecimales comienzan con `#` y utilizan normalmente seis caracteres.

```css
color: #ff0000;
```

Su estructura es:

```text
#RRGGBB
```

```text
RR → rojo
GG → verde
BB → azul
```

Los valores utilizan números del `0` al `9` y letras de la `a` a la `f`.

```css
color: #ff0000; /* Rojo */
color: #00ff00; /* Verde */
color: #0000ff; /* Azul */
color: #ffffff; /* Blanco */
color: #000000; /* Negro */
```

### RGB

RGB significa:

```text
Red   → rojo
Green → verde
Blue  → azul
```

Cada canal utiliza valores entre `0` y `255`.

```css
color: rgb(242, 102, 222);
```

Ejemplos:

```css
color: rgb(255, 0, 0);
color: rgb(0, 255, 0);
color: rgb(0, 0, 255);
```

### RGBA

RGBA agrega un valor alfa para controlar la transparencia.

```css
color: rgba(255, 0, 0, 0.5);
```

El valor alfa va de `0` a `1`.

```text
0   → transparente
0.5 → semitransparente
1   → opaco
```

### HSL

HSL significa:

```text
Hue        → tono
Saturation → saturación
Lightness  → luminosidad
```

```css
color: hsl(200, 100%, 50%);
```

#### Tono

Representa una posición dentro del círculo cromático.

```text
0°   → rojo
120° → verde
240° → azul
```

#### Saturación

Controla la intensidad del color.

```text
0%   → gris
100% → color intenso
```

#### Luminosidad

Controla qué tan claro u oscuro es el color.

```text
0%   → negro
50%  → color normal
100% → blanco
```

HSL también admite transparencia:

```css
color: hsla(200, 100%, 50%, 0.5);
```

---

# Texto

## `font-size`

Define el tamaño del texto.

```css
body {
    font-size: 25px;
}
```

Los píxeles pueden utilizarse para establecer tamaños concretos:

```css
font-size: 16px;
```

En interfaces web suele ser más conveniente usar unidades relativas como `rem`, porque se adaptan mejor a la configuración de tamaño del navegador.

```css
font-size: 1rem;
```

De forma predeterminada, `1rem` suele equivaler a `16px`.

Una forma habitual de definir el tamaño general es:

```css
body {
    font-size: 1rem;
}
```

## `font-family`

Define la fuente del texto.

```css
body {
    font-family: Arial;
}
```

Es conveniente incluir fuentes alternativas:

```css
body {
    font-family: Arial, Helvetica, sans-serif;
}
```

El navegador utiliza la primera fuente disponible.

Cuando una fuente contiene espacios, se escribe entre comillas:

```css
font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
```

## `text-decoration`

Controla decoraciones como el subrayado.

```css
.button {
    text-decoration: none;
}
```

Se utiliza frecuentemente para quitar el subrayado predeterminado de los enlaces.

---

# Propiedades de texto

## `text-align`

Define la alineación horizontal del contenido en línea.

```css
text-align: center;
```

Valores frecuentes:

```css
text-align: start;
text-align: center;
text-align: end;
text-align: justify;
```

```text
start   → inicio de la dirección del texto
center  → centro
end     → final de la dirección del texto
justify → distribuye el texto entre ambos extremos
```

En documentos escritos de izquierda a derecha, `start` suele representar el lado izquierdo.

---

## `text-transform`

Modifica visualmente el uso de mayúsculas y minúsculas.

```css
text-transform: uppercase;
```

Valores frecuentes:

```css
text-transform: uppercase;
text-transform: lowercase;
text-transform: capitalize;
text-transform: none;
```

```text
uppercase  → convierte el texto a mayúsculas
lowercase  → convierte el texto a minúsculas
capitalize → coloca en mayúscula el inicio de cada palabra
none       → no aplica transformación
```

La propiedad modifica la presentación visual, no el texto original escrito en HTML.

---

## `letter-spacing`

Controla el espacio entre caracteres.

```css
letter-spacing: 2px;
```

Un valor positivo aumenta la separación.

```css
letter-spacing: 5px;
```

Un valor negativo reduce la separación.

```css
letter-spacing: -1px;
```

Valores demasiado grandes o pequeños pueden dificultar la lectura.

---

## `word-spacing`

Controla el espacio entre palabras.

```css
word-spacing: 4px;
```

Debe utilizarse una unidad, excepto cuando el valor es `0`.

```css
word-spacing: 0;
word-spacing: -4px;
```

---

## `line-height`

Define la altura de cada línea de texto.

```css
line-height: 1.2;
```

Cuando se utiliza un número sin unidad, el valor se multiplica por el tamaño de la fuente.

```css
font-size: 30px;
line-height: 1.2;
```

El cálculo aproximado es:

```text
30px × 1.2 = 36px
```

Una forma habitual para párrafos es:

```css
line-height: 1.5;
```

No existe un único valor predeterminado igual en todos los navegadores y fuentes.

---

## `overflow-wrap`

Permite dividir palabras largas cuando no caben dentro de su contenedor.

```css
overflow-wrap: break-word;
```

Ejemplo:

```css
.title {
    width: 150px;
    overflow-wrap: break-word;
}
```

Sin esta propiedad, una palabra muy larga puede desbordar la caja.

```text
Sin overflow-wrap:

┌──────────────┐
│ palabraextremadamentelarga────────►
└──────────────┘

Con break-word:

┌──────────────┐
│ palabraextre │
│ madamentelar │
│ ga           │
└──────────────┘
```

---

## `hyphens`

Controla la separación de palabras mediante guiones.

```css
hyphens: auto;
```

Valores principales:

```css
hyphens: none;
hyphens: manual;
hyphens: auto;
```

`hyphens: auto` depende del idioma declarado en HTML y del soporte del navegador.

```html
<html lang="es">
```

No siempre divide palabras muy largas. Para evitar desbordamientos suele combinarse con:

```css
overflow-wrap: break-word;
```

---

# Fuentes web y variantes

## Fuentes de respaldo y fuentes web

Define la familia tipográfica.

```css
body {
    font-family: "Cabin", Arial, sans-serif;
}
```

El navegador intenta utilizar las fuentes en el orden escrito:

```text
1. Cabin
2. Arial
3. Cualquier fuente sans-serif disponible
```

Cuando el nombre de una fuente contiene espacios, debe escribirse entre comillas.

Google Fonts es un catálogo de fuentes web que permite cargar una familia tipográfica aunque no esté instalada en el dispositivo del usuario.

La fuente debe importarse o enlazarse antes de utilizarla.

---

## `font-weight`

Define el grosor del texto.

```css
font-weight: bold;
```

También puede utilizar valores numéricos:

```css
font-weight: 400;
font-weight: 700;
```

```text
400 → grosor normal
700 → negrita
```

Los grosores disponibles dependen de la familia tipográfica cargada.

---

## `font-style`

Define el estilo de la fuente.

```css
font-style: italic;
```

Valores frecuentes:

```css
font-style: normal;
font-style: italic;
font-style: oblique;
```

---

# Unidades de medida en CSS

CSS permite definir tamaños mediante unidades absolutas y relativas.

```css
width: 300px;
font-size: 1.5rem;
height: 50vh;
```

## Unidades absolutas

Las unidades absolutas representan medidas concretas.

```text
px → píxeles
cm → centímetros
mm → milímetros
pt → puntos
```

La unidad más utilizada en interfaces web es `px`.

```css
.caja {
    width: 300px;
    padding: 20px;
}
```

## Unidades relativas

Las unidades relativas calculan su tamaño a partir de otro valor.

```text
%   → relativo al elemento contenedor
em  → relativo al tamaño de fuente del elemento
rem → relativo al tamaño de fuente de html
vw  → relativo al ancho del viewport
vh  → relativo al alto del viewport
```

## Unidad `px`

`px` significa píxel.

Se utiliza para definir dimensiones y espacios:

```css
width: 200px;
height: 200px;
font-size: 20px;
padding: 10px;
margin: 30px;
border-width: 5px;
```

Es una unidad útil para:

* bordes;
* tamaños concretos;
* ejercicios del modelo de caja;
* separaciones pequeñas.

Para el tamaño del texto suele ser más conveniente utilizar unidades relativas como `rem`.

```css
font-size: 1rem;
```

## Porcentajes

El porcentaje se calcula normalmente a partir del tamaño del elemento contenedor.

```css
.hijo {
    width: 50%;
}
```

El elemento ocupará la mitad del ancho disponible de su padre.

```text
Contenedor: 600px
Hijo:        50%

600px × 0.5 = 300px
```

Para propiedades verticales como `height`, el porcentaje necesita que la altura del elemento padre esté definida.

```css
.padre {
    height: 400px;
}

.hijo {
    height: 50%;
}
```

El hijo tendrá una altura de `200px`.

## Unidad `rem`

`rem` es relativo al tamaño de fuente del elemento raíz `<html>`.

```css
html {
    font-size: 16px;
}
```

Con ese valor:

```text
1rem   = 16px
1.5rem = 24px
2rem   = 32px
```

Ejemplo:

```css
.primero {
    font-size: 1.5rem;
}
```

Si `html` utiliza `16px`, el texto tendrá un tamaño de `24px`.

```text
16px × 1.5 = 24px
```

`rem` es conveniente para definir tamaños de texto y espacios de forma consistente.

También permite que el diseño responda mejor a cambios en el tamaño de fuente configurado por el usuario.

## Unidad `em`

`em` se calcula a partir del tamaño de fuente del propio elemento.

Si el elemento no tiene un tamaño declarado, utiliza el tamaño de fuente heredado.

```css
.cuarto {
    font-size: 2em;
}
```

Si el tamaño heredado es de `16px`:

```text
16px × 2 = 32px
```

El tamaño final será de `32px`.

### `em` aplicado a otras propiedades

Cuando `em` se utiliza en propiedades como `padding`, se calcula a partir del `font-size` del propio elemento.

```css
.cuarto {
    font-size: 2em;
    padding: 2em 0;
}
```

Si el tamaño heredado era de `16px`:

```text
font-size: 2em
16px × 2 = 32px
```

El nuevo tamaño de fuente del elemento es `32px`.

El padding se calcula a partir de ese valor:

```text
padding: 2em
32px × 2 = 64px
```

Por lo tanto, el padding superior e inferior será de `64px`.

### Diferencia entre `em` y `rem`

```text
rem → toma como referencia el font-size de html
em  → toma como referencia el font-size del elemento
```

Ejemplo:

```css
html {
    font-size: 16px;
}

.elemento {
    font-size: 2rem;
}
```

```text
2rem = 16px × 2 = 32px
```

En cambio:

```css
.padre {
    font-size: 20px;
}

.hijo {
    font-size: 2em;
}
```

```text
2em = 20px × 2 = 40px
```

## Viewport

El viewport es el área visible de la página dentro del navegador.

```text
┌───────────────────────────────┐
│                               │
│       Área visible            │
│       del navegador           │
│                               │
└───────────────────────────────┘
```

El contenido que queda fuera de esa área puede verse mediante desplazamiento.

## Unidad `vw`

`vw` significa **viewport width**.

Cada unidad representa el `1%` del ancho del viewport.

```text
1vw   → 1% del ancho visible
30vw  → 30% del ancho visible
100vw → 100% del ancho visible
```

Ejemplo:

```css
.container {
    width: 30vw;
}
```

Si el viewport tiene `1000px` de ancho:

```text
1000px × 0.30 = 300px
```

El contenedor tendrá un ancho de `300px`.

## Unidad `vh`

`vh` significa **viewport height**.

Cada unidad representa el `1%` del alto del viewport.

```text
1vh   → 1% del alto visible
50vh  → 50% del alto visible
100vh → 100% del alto visible
```

Ejemplo:

```css
.container {
    height: 50vh;
}
```

Si el viewport tiene `800px` de alto:

```text
800px × 0.50 = 400px
```

El contenedor tendrá una altura de `400px`.

## Comparación entre `%`, `vw` y `vh`

```text
%  → depende del tamaño del elemento padre
vw → depende del ancho del viewport
vh → depende del alto del viewport
```

```css
.elemento {
    width: 50%;
}
```

Ocupa la mitad del ancho de su contenedor.

```css
.elemento {
    width: 50vw;
}
```

Ocupa la mitad del ancho visible del navegador.

```css
.elemento {
    height: 50vh;
}
```

Ocupa la mitad del alto visible del navegador.
# Modelo de caja

Cada elemento HTML se representa como una caja rectangular.

Está formada por cuatro partes:

```text
Contenido → Padding → Borde → Margin
```

```text
┌─────────────────────────────────────┐
│               Margin                │
│   ┌─────────────────────────────┐   │
│   │            Borde            │   │
│   │   ┌─────────────────────┐   │   │
│   │   │       Padding       │   │   │
│   │   │   ┌─────────────┐   │   │   │
│   │   │   │  Contenido  │   │   │   │
│   │   │   └─────────────┘   │   │   │
│   │   └─────────────────────┘   │   │
│   └─────────────────────────────┘   │
└─────────────────────────────────────┘
```

### Contenido

Es el espacio donde aparecen el texto, las imágenes u otros elementos.

### Padding

Es el espacio interno entre el contenido y el borde.

### Borde

Rodea el contenido y el padding.

### Margin

Es el espacio exterior que separa la caja de otros elementos.

---

# Ancho y alto

## `width`

Define el ancho de un elemento.

```css
.caja {
    width: 200px;
}
```

## `height`

Define la altura de un elemento.

```css
.caja {
    height: 200px;
}
```

## Ejemplo

```css
.caja {
    width: 200px;
    height: 200px;
    background-color: teal;
}
```

`height` establece una altura fija. Si el contenido necesita más espacio, puede desbordarse.

Para componentes cuyo contenido puede crecer, suele ser más conveniente establecer una altura mínima:

```css
.caja {
    min-height: 200px;
}
```

## Tamaño adaptable con `max-width`

### `max-width`

Define el ancho máximo que puede alcanzar un elemento.

```css
.card {
    width: 80%;
    max-width: 500px;
}
```

En este ejemplo:

* la tarjeta ocupa el `80%` del espacio disponible;
* nunca supera los `500px`.

Esto permite que el elemento se reduzca en pantallas pequeñas sin crecer demasiado en pantallas grandes.

```text
Contenedor pequeño → 80% del espacio
Contenedor grande  → máximo 500px
```

---

# Padding

El `padding` es el espacio interno entre el contenido y el borde.

```css
.caja {
    padding: 20px;
}
```

## Propiedades individuales

```css
padding-top: 20px;
padding-right: 20px;
padding-bottom: 20px;
padding-left: 20px;
```

## Shorthand

```css
padding: 20px;
padding: 10px 20px;
padding: 10px 20px 30px;
padding: 10px 20px 30px 40px;
```

El orden general es:

```text
arriba → derecha → abajo → izquierda
```

El uso de dos valores es frecuente:

```css
padding: 10px 20px;
```

```text
10px → arriba y abajo
20px → izquierda y derecha
```

---

# Bordes

Un borde tiene tres características principales:

* grosor;
* estilo;
* color.

## `border-width`

Define el grosor.

```css
border-width: 20px;
```

También puede configurarse por lado:

```css
border-top-width: 30px;
border-right-width: 10px;
border-bottom-width: 20px;
border-left-width: 5px;
```

## `border-style`

Define el estilo visual.

```css
border-style: solid;
```

Valores frecuentes:

```text
solid   → sólido
dotted  → puntos
dashed  → guiones
double  → doble
groove  → relieve
ridge   → relieve invertido
inset   → hacia dentro
outset  → hacia fuera
```

## `border-color`

Define el color.

```css
border-color: blue;
```

Para que el borde sea visible necesita un estilo:

```css
.caja {
    border-width: 10px;
    border-style: solid;
    border-color: blue;
}
```

## Shorthand de `border`

Permite definir grosor, estilo y color en una sola línea:

```css
border: 20px solid blue;
```

El orden recomendado es:

```text
grosor → estilo → color
```

---

# Margin

El `margin` es el espacio exterior de una caja.

```css
.caja {
    margin: 20px;
}
```

## Propiedades individuales

```css
margin-top: 20px;
margin-right: 20px;
margin-bottom: 20px;
margin-left: 20px;
```

## Shorthand

```css
margin: 20px;
margin: 10px 20px;
margin: 10px 20px 30px;
margin: 10px 20px 30px 40px;
```

El orden general es:

```text
arriba → derecha → abajo → izquierda
```

Ejemplo habitual:

```css
margin: 10px 20px;
```

```text
10px → arriba y abajo
20px → izquierda y derecha
```

---

# Centrado con `margin: auto`

El valor `auto` permite que el navegador calcule automáticamente el margen disponible.

```css
.caja {
    width: 200px;
    margin: 0 auto;
}
```

Significa:

```text
0    → margen superior e inferior
auto → margen izquierdo y derecho
```

El espacio horizontal disponible se distribuye entre ambos lados.

```text
Espacio izquierdo | Caja | Espacio derecho
       auto        |200px|       auto
```

Para que funcione normalmente se necesita:

* una caja de bloque;
* un ancho menor que el espacio disponible;
* un `width` definido.

La forma completa es:

```css
.caja {
    width: 200px;
    margin-top: 0;
    margin-right: auto;
    margin-bottom: 0;
    margin-left: auto;
}
```

La forma habitual es:

```css
.caja {
    width: 200px;
    margin: 0 auto;
}
```

---

# Colapso de márgenes

Algunos márgenes verticales de cajas de bloque pueden colapsar.

En lugar de sumarse, suele conservarse el valor mayor.

```css
.main {
    margin-bottom: 30px;
}

.footer {
    margin-top: 50px;
}
```

La separación no será normalmente de `80px`.

```text
30px + 50px ≠ 80px
```

El resultado será:

```text
50px
```

Los márgenes horizontales no colapsan de esta manera.

El colapso puede ocurrir entre:

* elementos hermanos de bloque;
* un padre y su primer hijo;
* un padre y su último hijo;
* ciertos elementos vacíos.

## Colapso entre el margen del hijo y el padre

Un margen superior aplicado al primer hijo puede colapsar con el margen del elemento padre.

```css
h2 {
    margin-top: 50px;
}
```

Si `h2` es el primer hijo de `.background`, el margen puede desplazarse fuera del contenedor.

En el ejercicio se utiliza:

```css
.background {
    padding: 0.1px;
}
```

Ese pequeño `padding` separa el margen del hijo del borde del padre y evita el colapso.

Es una técnica válida para observar el comportamiento, aunque en un diseño real suele utilizarse un `padding` con una medida visual intencional:

```css
.background {
    padding-top: 50px;
}

h2 {
    margin-top: 0;
}
```

---

# `box-sizing`

`box-sizing` determina cómo se calcula el tamaño de una caja.

Sus valores principales son:

```css
box-sizing: content-box;
box-sizing: border-box;
```

## `content-box`

Es el valor predeterminado.

Con `content-box`, `width` y `height` representan únicamente el contenido.

```css
.element {
    box-sizing: content-box;
    width: 250px;
    padding: 30px;
    border: 30px solid blue;
}
```

El ancho total es:

```text
Contenido:       250px
Padding total:    60px
Borde total:      60px
─────────────────────
Ancho total:     370px
```

```text
250px + 60px + 60px = 370px
```

## `border-box`

Con `border-box`, `width` y `height` incluyen el contenido, el padding y el borde.

```css
.element {
    box-sizing: border-box;
    width: 250px;
    padding: 30px;
    border: 30px solid blue;
}
```

El ancho exterior se mantiene en `250px`.

```text
Ancho total:        250px
Padding total:       60px
Borde total:         60px
Contenido restante: 130px
```

```text
250px - 60px - 60px = 130px
```

## Comparación

| Característica      | `content-box` | `border-box` |
| ------------------- | ------------: | -----------: |
| `width` declarado   |         250px |        250px |
| Ancho del contenido |         250px |        130px |
| Ancho exterior      |         370px |        250px |

La forma habitual de simplificar el cálculo de las cajas es:

```css
* {
    box-sizing: border-box;
}
```

---

# Tipos de caja

La propiedad `display` determina cómo se comporta un elemento dentro de la página.

Los valores básicos son:

```css
display: block;
display: inline;
display: inline-block;
```

## `block`

Una caja de bloque:

* comienza en una nueva línea;
* ocupa normalmente todo el ancho disponible;
* acepta `width` y `height`;
* acepta padding y margin.

```css
.block {
    display: block;
    background-color: teal;
    color: white;
}
```

Elementos que suelen ser de bloque:

```html
<div></div>
<section></section>
<main></main>
<header></header>
<footer></footer>
<p></p>
```

## `inline`

Una caja en línea:

* no genera un salto de línea;
* ocupa el espacio necesario para su contenido;
* continúa junto a otros elementos;
* no acepta `width` y `height` de la misma forma que un bloque.

```css
.inline {
    display: inline;
    background-color: purple;
    color: white;
}
```

Elementos que suelen ser en línea:

```html
<span></span>
<a></a>
<strong></strong>
<em></em>
```

Los paddings horizontales se aplican normalmente. Los paddings verticales pueden verse, pero no separan las líneas de la misma forma que una caja de bloque.

## `inline-block`

Combina características de `inline` y `block`.

* permanece en la misma línea;
* acepta `width` y `height`;
* acepta padding y margin;
* no ocupa automáticamente todo el ancho.

```css
.button {
    display: inline-block;
    padding: 15px 30px;
}
```

Es útil para enlaces con apariencia de botón.

## Comparación

| Característica                    |        `block` |       `inline` | `inline-block` |
| --------------------------------- | -------------: | -------------: | -------------: |
| Nueva línea                       |             Sí |             No |             No |
| Ocupa el ancho disponible         |    Normalmente |             No |             No |
| Acepta `width` y `height`         |             Sí | No normalmente |             Sí |
| Permanece junto a otros elementos | No normalmente |             Sí |             Sí |

```text
BLOCK

┌─────────────────────────────────┐
│ Elemento uno                    │
└─────────────────────────────────┘
┌─────────────────────────────────┐
│ Elemento dos                    │
└─────────────────────────────────┘

INLINE

Texto [Elemento uno] [Elemento dos] texto.

INLINE-BLOCK

[ Elemento uno ] [ Elemento dos ]
```

## Imágenes como elementos de bloque

Una imagen es un elemento en línea de forma predeterminada.

Para centrarla horizontalmente con `margin: 0 auto`, puede convertirse en bloque:

```css
.img {
    width: 200px;
    display: block;
    margin: 0 auto;
}
```

```text
display: block
→ permite que los márgenes automáticos ocupen
  el espacio disponible a ambos lados.
```

---

# Fondos

## `background-color`

Define el color de fondo de un elemento.

```css
.title {
    background-color: antiquewhite;
}
```

También puede utilizarse junto con una imagen de fondo:

```css
.background {
    background-color: blanchedalmond;
    background-image: url("images/pangolin.png");
}
```

Si la imagen no carga o no ocupa toda la caja, se verá el color de fondo.

## `background-image`

Coloca una imagen como fondo de un elemento.

```css
.background {
    background-image: url("images/pangolin.png");
}
```

`url()` recibe la ruta del archivo.

Las imágenes de fondo se utilizan principalmente con fines visuales o decorativos.

Si una imagen aporta información importante, es más adecuado utilizar la etiqueta HTML `<img>` con su atributo `alt`.

## `background-repeat`

Por defecto, una imagen de fondo se repite si no ocupa todo el elemento.

```css
background-repeat: repeat;
```

Para evitar la repetición:

```css
background-repeat: no-repeat;
```

Otros valores son:

```css
background-repeat: repeat-x;
background-repeat: repeat-y;
```

```text
repeat    → repite en ambos ejes
repeat-x  → repite horizontalmente
repeat-y  → repite verticalmente
no-repeat → no repite
```

## `background-size`

Define el tamaño de la imagen de fondo.

### Tamaño específico

```css
background-size: 100px;
```

La imagen tendrá un ancho de `100px` y conservará normalmente sus proporciones.

También pueden definirse ancho y alto:

```css
background-size: 100px 150px;
```

```text
100px → ancho
150px → alto
```

### `contain`

```css
background-size: contain;
```

Ajusta la imagen para mostrarla completa dentro del elemento.

Puede dejar espacios sin cubrir si la proporción de la imagen es diferente a la del contenedor.

### `cover`

```css
background-size: cover;
```

Ajusta la imagen para cubrir todo el elemento.

Puede recortar parte de la imagen para conservar sus proporciones.

```text
contain → muestra la imagen completa
cover   → cubre todo el contenedor
```

## `background-position`

Define la posición de la imagen dentro del elemento.

```css
background-position: center;
```

Valores frecuentes:

```css
background-position: top;
background-position: right;
background-position: bottom;
background-position: left;
background-position: center;
```

También pueden combinarse:

```css
background-position: top left;
background-position: bottom right;
background-position: center center;
```

El primer valor representa normalmente la posición horizontal y el segundo la vertical.

```css
background-position: right top;
```

También pueden utilizarse medidas:

```css
background-position: 20px 40px;
```

```text
20px → posición horizontal
40px → posición vertical
```

La posición inicial es la esquina superior izquierda:

```css
background-position: 0% 0%;
```

## Degradados

La función `linear-gradient()` crea una transición gradual entre dos o más colores.

```css
background-image: linear-gradient(
    rgba(52, 23, 7, 0.3),
    rgba(62, 24, 0, 0.3)
);
```

Un degradado puede combinarse con una imagen de fondo:

```css
background-image:
    linear-gradient(
        rgba(52, 23, 7, 0.3),
        rgba(62, 24, 0, 0.3)
    ),
    url("images/pangolin.png");
```

Las capas se dibujan de izquierda a derecha:

```text
Primera capa → degradado
Segunda capa → imagen
```

El degradado debe utilizar colores con transparencia para permitir que la imagen inferior sea visible.

```text
Alfa 0   → transparente
Alfa 0.3 → parcialmente transparente
Alfa 1   → opaco
```

Por lo tanto, `rgba(..., 0.3)` es semitransparente, no opaco.

## Formatos de imagen

### JPG

JPG es adecuado para fotografías e imágenes con muchos colores.

Utiliza compresión con pérdida, por lo que puede perder calidad.

### PNG

PNG permite transparencia y se utiliza en ilustraciones, capturas y elementos gráficos.

Está formado por píxeles, por lo que puede perder nitidez al ampliarse por encima de su resolución.

### SVG

SVG es un formato vectorial.

Puede ampliarse sin perder definición porque describe las formas mediante información matemática.

Es adecuado para:

* logotipos;
* iconos;
* ilustraciones simples;
* figuras geométricas.
# Posicionamiento en CSS

La propiedad `position` define cómo se ubica un elemento dentro de la página.

Sus valores principales son:

```css
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

Las propiedades de desplazamiento son:

```css
top
right
bottom
left
```

Estas propiedades no producen el mismo efecto con todos los valores de `position`.

## `position: static`

`static` es el valor predeterminado de los elementos.

```css
.elemento {
    position: static;
}
```

El elemento permanece dentro del flujo normal del documento.

Las propiedades `top`, `right`, `bottom` y `left` no modifican su posición.

```css
.static {
    position: static;
    background-color: darkblue;
}
```

Normalmente no es necesario declarar `position: static`, porque ya es el comportamiento inicial.

## Flujo normal del documento

El flujo normal es la forma en la que el navegador distribuye los elementos de manera predeterminada.

```text
┌──────────────────┐
│ Elemento 1       │
└──────────────────┘
┌──────────────────┐
│ Elemento 2       │
└──────────────────┘
┌──────────────────┐
│ Elemento 3       │
└──────────────────┘
```

Los elementos ocupan espacio y afectan la posición de los demás.

## `position: relative`

`relative` mantiene el elemento dentro del flujo normal, pero permite moverlo desde su posición original.

```css
.relative {
    position: relative;
    left: 30px;
}
```

El elemento se desplaza `30px` desde la izquierda de su posición original.

```text
Posición original
┌──────────────┐
│              │
└──────────────┘

         Elemento desplazado
         ┌──────────────┐
         │              │
         └──────────────┘
```

El espacio original continúa reservado, aunque el elemento se haya desplazado.

Puede utilizar:

```css
top: 20px;
right: 20px;
bottom: 20px;
left: 20px;
```

Las propiedades indican desde qué lado se desplaza el elemento.

```css
left: 30px;
```

lo mueve hacia la derecha.

```css
top: 30px;
```

lo mueve hacia abajo.

## Uso de `relative` como referencia

Un elemento con `position: relative` también puede funcionar como referencia para un hijo con `position: absolute`.

```css
.container {
    position: relative;
}

.elemento {
    position: absolute;
    right: 30px;
}
```

En este caso, `.elemento` se posiciona tomando como referencia a `.container`.

## `position: absolute`

`absolute` retira el elemento del flujo normal.

```css
.absolute {
    position: absolute;
    right: 30px;
}
```

El elemento deja de reservar su espacio original, por lo que otros elementos pueden ocuparlo.

```text
Flujo normal:

┌──────────────┐
│ Elemento 1   │
└──────────────┘
┌──────────────┐
│ Elemento 2   │
└──────────────┘

Con absolute:

┌──────────────┐
│ Elemento 2   │
└──────────────┘

                    ┌──────────────┐
                    │ Elemento 1   │
                    └──────────────┘
```

Un elemento absoluto se posiciona tomando como referencia:

1. El ancestro más cercano cuya propiedad `position` no sea `static`.
2. Si no existe, utiliza como referencia el bloque inicial de la página.

La forma habitual es:

```css
.container {
    position: relative;
}

.absolute {
    position: absolute;
    top: 20px;
    right: 30px;
}
```

## `position: fixed`

`fixed` retira el elemento del flujo normal y lo posiciona respecto del viewport.

```css
.fixed {
    position: fixed;
    right: 20px;
    bottom: 20px;
}
```

El elemento permanece en el mismo lugar aunque la página se desplace.

```text
┌──────────────────────────────┐
│                              │
│                              │
│                     ┌──────┐ │
│                     │ fijo │ │
│                     └──────┘ │
└──────────────────────────────┘
```

Se utiliza frecuentemente para:

* botones flotantes;
* accesos rápidos;
* botones de mensajería;
* barras fijas;
* avisos permanentes.

## `position: sticky`

`sticky` combina características de `relative` y `fixed`.

```css
.sticky {
    position: sticky;
    top: 30px;
}
```

El elemento se comporta inicialmente como parte del flujo normal.

Cuando alcanza la distancia indicada, permanece fijo dentro de los límites de su contenedor.

```text
Antes de llegar a top: 30px
→ se desplaza con el contenido.

Al llegar a top: 30px
→ permanece pegado a esa posición.
```

Para que funcione debe indicarse al menos una referencia, como:

```css
top: 30px;
```

También puede utilizar:

```css
bottom
left
right
```

Su funcionamiento depende del espacio disponible y del contenedor al que pertenece.

## Comparación

| Valor      | Ocupa su espacio original | Referencia principal         | Sigue el desplazamiento |
| ---------- | ------------------------: | ---------------------------- | ----------------------: |
| `static`   |                        Sí | Flujo normal                 |                      Sí |
| `relative` |                        Sí | Su posición original         |                      Sí |
| `absolute` |                        No | Ancestro posicionado         |                      Sí |
| `fixed`    |                        No | Viewport                     |                      No |
| `sticky`   |                        Sí | Contenedor y límite indicado |            Parcialmente |

## `z-index`

`z-index` controla el orden de superposición de los elementos.

```css
.elemento {
    position: relative;
    z-index: 2;
}
```

Cuando dos elementos se superponen, el que tenga el valor mayor suele mostrarse por encima.

```text
z-index: 3 → capa superior
z-index: 2 → capa intermedia
z-index: 1 → capa inferior
```

Ejemplo:

```css
.primero {
    position: relative;
    z-index: 1;
}

.segundo {
    position: relative;
    z-index: 2;
}
```

`.segundo` se mostrará encima de `.primero` cuando ambos se superpongan.

`z-index` se aplica principalmente a elementos posicionados con:

```css
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

Un valor alto no garantiza que un elemento aparezca por encima de toda la página, porque también depende del contexto de apilamiento de sus elementos padres.

---

# Sobrescritura de propiedades

Cuando una propiedad se repite dentro de la misma regla, se utiliza normalmente el último valor válido.

```css
.caja {
    color: red;
    color: white;
}
```

El texto será blanco.

## Ejemplo con distintos formatos de color

```css
.title {
    color: darkslateblue;
    color: rgb(242, 102, 222);
    color: #ff0000;
    color: hsl(200, 100%, 50%);
}
```

Aunque las cuatro declaraciones muestran formas válidas de escribir colores, el valor aplicado será:

```css
color: hsl(200, 100%, 50%);
```

porque es la última declaración válida.

## Sobrescritura mediante shorthand

```css
.caja {
    border-width: 10px;
    border-style: dotted;
    border-color: black;

    border: 20px solid blue;
}
```

La última declaración reemplaza las propiedades anteriores del borde.

El resultado será:

```text
Grosor: 20px
Estilo: solid
Color: azul
```

También ocurre con `margin`:

```css
.caja {
    margin-top: 10px;
    margin-right: 20px;

    margin: 50px;
}
```

El último `margin` establece `50px` en los cuatro lados.

---

# Selector universal y reset

El selector universal selecciona todos los elementos:

```css
*
```

Ejemplo:

```css
* {
    box-sizing: border-box;
    margin: 0;
}
```

## `box-sizing: border-box`

Hace que el ancho y el alto incluyan el padding y el borde.

## `margin: 0`

Establece en cero los márgenes de todos los elementos seleccionados.

Esto también elimina los márgenes predeterminados de títulos, párrafos y listas.

Por eso, los espacios necesarios deben agregarse posteriormente mediante CSS.

---

# Ejemplo práctico: modelo de caja y tipos de caja

```css
/*
RESET BÁSICO

El selector universal selecciona todos los elementos.

border-box hace que width y height incluyan
el padding y el borde.

margin: 0 elimina los márgenes
de los elementos seleccionados.
*/

* {
    box-sizing: border-box;
    margin: 0;
}

body {
    font-size: 25px;
}

.element {
    width: 250px;
    height: 250px;
    background-color: teal;
    border: 30px solid blue;
    padding: 30px;
    margin: 0 auto;
}

.block {
    display: block;
    background-color: teal;
    color: white;
    margin-bottom: 30px;
}

.inline {
    display: inline;
    background-color: purple;
    color: white;
}

.button {
    display: inline-block;
    background-color: brown;
    color: azure;
    text-decoration: none;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    border-radius: 30px;
    padding: 15px 30px;
}
```

## Explicación

```css
* {
    box-sizing: border-box;
    margin: 0;
}
```

Aplica `border-box` y elimina los márgenes de todos los elementos.

```css
body {
    font-size: 25px;
}
```

Establece el tamaño general del texto.

```css
.element {
    width: 250px;
    height: 250px;
    background-color: teal;
    border: 30px solid blue;
    padding: 30px;
    margin: 0 auto;
}
```

Crea una caja de `250px`, con fondo, borde, padding y centrado horizontal.

Gracias a `border-box`, el borde y el padding quedan incluidos dentro de los `250px`.

```css
.block {
    display: block;
}
```

Crea una caja de bloque.

```css
.inline {
    display: inline;
}
```

Crea una caja en línea.

```css
.button {
    display: inline-block;
}
```

Permite que el enlace permanezca en línea y acepte padding como una caja de bloque.

---

# Ejemplo práctico: colores y fondos

```css
* {
    margin: 0;
    box-sizing: border-box;
}

.title {
    margin: 70px;

    /*
    La propiedad color se repite para comparar
    distintas formas de representar colores.

    CSS aplica el último valor válido.
    */

    color: darkslateblue;
    color: rgb(242, 102, 222);
    color: #ff0000;
    color: hsl(200, 100%, 50%);

    background-color: antiquewhite;
}

.background {
    width: 300px;
    height: 300px;
    margin: 50px;

    background-color: blanchedalmond;
    background-image: url("images/pangolin.png");
    background-size: 100px;
    background-repeat: no-repeat;
    background-position: center;
}
```

En `.title`, el color aplicado es:

```css
color: hsl(200, 100%, 50%);
```

porque es la última declaración válida de `color`.

En `.background`:

* `background-color` define el color de fondo;
* `background-image` agrega la imagen;
* `background-size` establece su tamaño;
* `background-repeat` evita que se repita;
* `background-position` centra la imagen.

---

# Ejemplo práctico: unidades de medida

```css
* {
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, Helvetica, sans-serif;
}

.container {
    padding: 30px;
    background-color: blueviolet;
    color: azure;
}

.primero {
    font-size: 1.5rem;
}

.segundo,
.tercero {
    font-size: 24px;
}

.cuarto {
    font-size: 2em;
    padding: 2em 0;
}
```

En este ejemplo:

* `.primero` utiliza una medida relativa al elemento `html`;
* `.segundo` y `.tercero` utilizan una medida fija en píxeles;
* `.cuarto` utiliza `em`, por lo que su tamaño depende del tamaño de fuente heredado;
* el `padding` de `.cuarto` se calcula a partir de su propio `font-size`.

---

# Ejemplo práctico: posicionamiento

```css
* {
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, Helvetica, sans-serif;
}

.container {
    width: 90%;
    height: 500px;
    margin: 80px auto;
    border: 2px solid darkgray;
}

.position {
    width: 150px;
    height: 100px;
    color: aliceblue;
    font-size: 1.3rem;
    line-height: 100px;
    text-align: center;
}

.static {
    background-color: darkblue;
    position: static;
}

.relative {
    background-color: tomato;
    position: relative;
    left: 30px;
}

.absolute {
    background-color: purple;
    position: absolute;
    right: 30px;
}

.fixed {
    background-color: cadetblue;
    position: fixed;
}

.sticky {
    width: 140px;
    height: 140px;
    background-color: slateblue;
    position: sticky;
    top: 30px;
}
```
