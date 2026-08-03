# Biblioteca de conceptos CSS

Esta biblioteca reúne definiciones, ejemplos y relaciones entre los conceptos de CSS estudiados. Los temas están organizados desde los fundamentos hasta propiedades de texto, unidades, fondos, posicionamiento y flexbox.

## Índice

* [Selector de clase](#selector-de-clase)
* [Selectores combinados](#selectores-combinados)
* [Pseudoclases y pseudoelementos](#pseudoclases-y-pseudoelementos)
* [Colores](#colores)
* [Texto](#texto)
* [Propiedades de texto](#propiedades-de-texto)
* [Fuentes web y variantes](#fuentes-web-y-variantes)
* [Unidades de medida en CSS](#unidades-de-medida-en-css)
* [Modelo de caja](#modelo-de-caja)
* [Ancho y alto](#ancho-y-alto)
* [Padding](#padding)
* [Bordes](#bordes)
* [Sombras](#sombras)
* [Margin](#margin)
* [Centrado con `margin: auto`](#centrado-con-margin-auto)
* [Colapso de márgenes](#colapso-de-márgenes)
* [`box-sizing`](#box-sizing)
* [Tipos de caja](#tipos-de-caja)
* [Fondos](#fondos)
* [Posicionamiento en CSS](#posicionamiento-en-css)
* [Flexbox](#flexbox)
* [Variables CSS (Custom Properties)](#variables-css-custom-properties)
* [Grid](#grid)
* [Media Queries](#media-queries)
* [Transform](#transform)
* [Transiciones](#transiciones)
* [Animaciones](#animaciones)
* [Metodología BEM](#metodología-bem)
* [Sobrescritura de propiedades](#sobrescritura-de-propiedades)
* [Selector universal y reset](#selector-universal-y-reset)
* [Ejemplo práctico: modelo de caja y tipos de caja](#ejemplo-práctico-modelo-de-caja-y-tipos-de-caja)
* [Ejemplo práctico: colores y fondos](#ejemplo-práctico-colores-y-fondos)
* [Ejemplo práctico: unidades de medida](#ejemplo-práctico-unidades-de-medida)
* [Ejemplo práctico: posicionamiento](#ejemplo-práctico-posicionamiento)
* [Ejemplo práctico: card (bordes y sombras)](#ejemplo-práctico-card-bordes-y-sombras)
* [Ejemplo práctico: flexbox](#ejemplo-práctico-flexbox)
* [Ejemplo práctico: variables CSS](#ejemplo-práctico-variables-css)
* [Ejemplo práctico: grid](#ejemplo-práctico-grid)
* [Ejemplo práctico: media queries](#ejemplo-práctico-media-queries)
* [Ejemplo práctico: selectores, pseudoclases y pseudoelementos](#ejemplo-práctico-selectores-pseudoclases-y-pseudoelementos)
* [Ejemplo práctico: transform](#ejemplo-práctico-transform)
* [Ejemplo práctico: box-shadow y border-radius](#ejemplo-práctico-box-shadow-y-border-radius)
* [Ejemplo práctico: transiciones](#ejemplo-práctico-transiciones)
* [Ejemplo práctico: animaciones](#ejemplo-práctico-animaciones)
* [Ejemplo práctico: landing page (grid responsive + BEM)](#ejemplo-práctico-landing-page-grid-responsive--bem)
* [Ejemplo práctico: formulario animado (floating label)](#ejemplo-práctico-formulario-animado-floating-label)

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

# Selectores combinados

Un selector combinado (o combinador) selecciona elementos según su relación con otro elemento, en vez de seleccionarlos directamente por su clase, id o tipo.

## Selector de hermano adyacente (`+`)

Selecciona únicamente al hermano que aparece inmediatamente después del elemento de referencia.

```css
.btn-red + .btn-purple {
    background-color: blue;
}
```

```text
elemento_referencia + .hermano_siguiente { ... }
```

Por ejemplo, si el HTML tiene dos elementos `<a>` seguidos, el selector `a + a` selecciona únicamente al segundo `<a>`, el que sigue inmediatamente después del primero.

```html
<a class="btn-red">Uno</a>
<a class="btn-purple">Dos</a>
```

```text
.btn-red + .btn-purple
→ selecciona "Dos", porque viene inmediatamente después de .btn-red
```

## Selector de hermano general (`~`)

A diferencia de `+` (que selecciona solo al hermano inmediato), `~` selecciona a **todos** los hermanos que aparecen después del elemento de referencia, sin importar si están pegados o no.

```css
.form__input:focus ~ .form__line {
    transform: scale(1);
}
```

```text
elemento_referencia ~ .hermano_posterior { ... }
```

```html
<input class="form__input" />
<label class="form__label">Nombre</label>
<span class="form__line"></span>
```

```text
.form__input ~ .form__label → selecciona .form__label
.form__input ~ .form__line  → selecciona .form__line
```

Ambos elementos son hermanos posteriores de `.form__input`, aunque `.form__line` no esté pegado inmediatamente después.

```text
+ → solo el hermano inmediato siguiente
~ → todos los hermanos siguientes
```

## Selector universal combinado

El selector universal (`*`) también puede combinarse con otro selector, para seleccionar todos los descendientes de un elemento.

```css
.btn-red * {
    background-color: green;
}
```

Esto selecciona a todos los elementos descendientes de `.btn-red` (sus hijos, nietos, etc.), sin importar su tipo o clase.

---

# Pseudoclases y pseudoelementos

## Pseudoclases

Una pseudoclase selecciona un elemento según un estado o condición particular, no según su tipo o clase. Se escriben con dos puntos (`:`).

```css
selector:pseudoclase {
    propiedad: valor;
}
```

Existen muchas pseudoclases además de las siguientes.

### `:hover`

Indica cuando el usuario pasa el cursor sobre el elemento.

```css
.btn-red:hover {
    transform: scale(1.2);
}
```

En computadora ocurre al pasar el mouse por encima. En un dispositivo táctil, ocurre al tocar el elemento.

### `:active`

Indica cuando el usuario hace click sobre el elemento.

```css
.btn-purple:active {
    transform: scale(1.2);
}
```

En computadora ocurre al hacer click. En un dispositivo táctil, ocurre al mantener presionado el elemento.

### `:focus`

Indica cuando un elemento que puede recibir foco (como un `input`, `textarea` o `select`) está activo/seleccionado.

```css
.input:focus {
    border: 2px solid blue;
}
```

### `:placeholder-shown`

Indica cuando un `input` está mostrando su `placeholder`; es decir, cuando el campo está **vacío** (todavía no se escribió nada, y no tiene foco con contenido).

```css
.form__input:placeholder-shown {
    border-color: gray;
}
```

En cuanto el usuario escribe algo (o el campo tiene un valor), el `placeholder` deja de mostrarse y la pseudoclase deja de aplicar.

### `:not()`

Es una pseudoclase de negación: selecciona los elementos que **no** cumplen con el selector indicado adentro del paréntesis.

```css
.form__input:not(:placeholder-shown) {
    border-color: var(--main-color);
}
```

```text
:not(:placeholder-shown) → selecciona el input cuando NO está mostrando
                            su placeholder, es decir, cuando tiene contenido
```

`:not()` puede combinarse con cualquier otro selector o pseudoclase, no solo con `:placeholder-shown`.

### `:checked`

Indica que un elemento como un checkbox o un radio button está seleccionado. Suele combinarse con el selector de hermano adyacente para estilizar otro elemento según ese estado.

```css
.check:checked + .label {
    background-color: green;
    transform: scale(1.2);
}
```

### `:target`

Indica cuando el usuario hace click sobre un enlace que apunta al `id` de un elemento del documento (mediante `href="#id"`).

```css
#seccion:target {
    background-color: yellow;
}
```

### `:root`

Ya se vio en la sección de [Variables CSS](#variables-css-custom-properties): representa el elemento raíz del documento.

## Pseudoelementos

Un pseudoelemento permite estilizar una parte específica de un elemento, o insertar contenido generado por CSS. Se escriben con dos puntos dobles (`::`).

```css
selector::pseudoelemento {
    propiedad: valor;
}
```

### `::before` y `::after`

Crean un elemento adicional antes o después del contenido de un elemento.

```css
.element::after {
    content: "";
}
```

```text
::before → inserta contenido antes del contenido del elemento
::after  → inserta contenido después del contenido del elemento
```

Solo puede existir un `::before` y un `::after` por elemento. Ambos necesitan la propiedad `content` para poder mostrarse, aunque sea un valor vacío (`content: ""`). Fuera de eso, aceptan cualquier otra propiedad CSS (tamaño, color, posición, etc.), igual que un elemento normal.

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

En navegadores modernos, `rgb()` también acepta un cuarto valor de alfa directamente, sin necesidad de escribir `rgba()`:

```css
box-shadow: 0 5px 10px -5px rgb(0, 0, 0, 0.3);
```

Ambas formas (`rgb()` con 4 valores y `rgba()`) funcionan igual; `rgba()` sigue siendo más explícita y ampliamente reconocida.

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

## `opacity`

Mientras que el alfa de `rgba()`/`hsla()` controla la transparencia de un solo color, `opacity` controla la transparencia de **todo el elemento**, incluido su contenido, sus bordes y su sombra.

```css
.element {
    opacity: 0.85;
}
```

```text
0   → completamente transparente
1   → completamente opaco (valor por defecto)
0.85 → casi opaco, con un poco de transparencia
```

```text
rgba(color, alfa) → transparencia solo de ese color puntual
opacity            → transparencia de todo el elemento en conjunto
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

## Tamaños intrínsecos: `max-content`, `min-content` y `fit-content`

Además de valores fijos (`px`) o relativos (`%`), `width` y `height` aceptan palabras clave que calculan el tamaño según el propio contenido del elemento.

```css
.element {
    width: max-content;
}
```

```text
max-content → el elemento ocupa el ancho necesario para mostrar su
              contenido sin cortarlo ni hacer saltos de línea innecesarios
min-content → el elemento ocupa el ancho mínimo posible, cortando el
              contenido (por ejemplo, texto) en tantas líneas como sea necesario
fit-content → se comporta como max-content, pero sin superar el ancho
              disponible del contenedor (combina lo mejor de ambos)
```

```css
.attribution {
    width: fit-content;
}
```

Son útiles para cajas que deben ajustarse exactamente a su contenido (como una etiqueta o un botón), sin necesidad de calcular un `width` fijo a mano.

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

## `border-radius`

Redondea las esquinas de un elemento.

```css
border-radius: 1em;
```

También puede definirse esquina por esquina. El orden es: superior-izquierda, superior-derecha, inferior-derecha, inferior-izquierda.

```css
border-radius: 1em 1em 0 0;
```

Ejemplo: redondear solo las esquinas superiores (útil para la imagen de una tarjeta que va pegada a un contenedor con esquinas inferiores redondeadas):

```text
 ╭───────────────╮
 │                │
 │                │
 └───────────────┘
```

```css
.card-img {
    border-radius: 1em 1em 0 0;
}

.card-container {
    border-radius: 0 0 1em 1em;
}
```

De esta forma, la imagen y el contenedor de texto de una misma tarjeta se combinan visualmente como si fueran una sola caja con las cuatro esquinas redondeadas.

### Esquinas individuales

A diferencia del shorthand `border-radius` (que reparte los valores en un orden fijo), estas propiedades permiten redondear una sola esquina a la vez, de forma independiente:

```css
border-top-left-radius: 10px;
border-top-right-radius: 10px;
border-bottom-left-radius: 10px;
border-bottom-right-radius: 10px;
```

### Truco: crear un círculo

Un cuadrado (mismo `width` y `height`) con `border-radius: 50%` se convierte visualmente en un círculo.

```css
.circulo {
    width: 4em;
    height: 4em;
    border-radius: 50%;
}
```

```text
┌─────────┐        ╭───────╮
│         │        │       │
│ cuadrado│  ───►   │círculo│
│         │        │       │
└─────────┘        ╰───────╯
   width = height        border-radius: 50%
```

## `outline`

`outline` dibuja un contorno alrededor de un elemento, de forma similar a `border`.

```css
outline: 3px solid black;
```

La diferencia principal es que `outline` **no forma parte del modelo de caja**: no ocupa espacio ni afecta el tamaño ni la posición del elemento ni de sus vecinos.

```text
border  → forma parte del box model, ocupa espacio dentro de la caja
outline → no forma parte del box model, se dibuja "por fuera", sin desplazar nada
```

---

# Sombras

## `box-shadow`

Aplica una o varias sombras alrededor de la caja de un elemento.

```css
box-shadow: 0 0 3px;
```

Sintaxis general (valores más comunes):

```text
box-shadow: offset-x offset-y blur-radius color;
```

```text
offset-x    → desplazamiento horizontal de la sombra
offset-y    → desplazamiento vertical de la sombra
blur-radius → qué tan difuminada se ve (a mayor valor, más difusa)
color       → color de la sombra (opcional; si se omite, suele usar el color del texto)
```

Ejemplo:

```css
.card {
    box-shadow: 0 0 3px;
}
```

```text
0 0 3px
offset-x: 0      → sin desplazamiento horizontal
offset-y: 0      → sin desplazamiento vertical
blur-radius: 3px → sombra difuminada de 3px alrededor de toda la caja
```

```text
┌───────────────────┐
│                    │
│      Contenido     │
│                    │
└───────────────────┘
  ░░░░░░░░░░░░░░░░░░░   ← sombra difuminada alrededor de la caja
```

Es una propiedad útil para dar sensación de profundidad, sin necesidad de agregar un borde visible.

## Detalles de `box-shadow`

`box-shadow` necesita, como mínimo, dos valores: el desplazamiento en `x` y en `y`.

```css
box-shadow: 10px 10px;
```

```text
offset-x
positivo → desplaza la sombra hacia la derecha
negativo → desplaza la sombra hacia la izquierda

offset-y
positivo → desplaza la sombra hacia abajo
negativo → desplaza la sombra hacia arriba
```

En cierto sentido, `box-shadow` funciona como un "calco" de la caja del elemento, desplazado y difuminado.

El tercer valor (opcional) es el `blur-radius`, que controla el difuminado:

```css
box-shadow: 10px 10px 1em;
```

Un `blur-radius` de `0` (o directamente omitido) genera una sombra nítida, sin difuminar.

El cuarto valor (opcional) es el color de la sombra. Si se omite, el navegador suele usar el color de texto del elemento (`currentColor`).

```css
box-shadow: 10px 10px 1em rgba(0, 0, 0, 0.5);
```

### Varias sombras a la vez

Se pueden aplicar múltiples sombras sobre el mismo elemento separándolas con comas.

```css
box-shadow:
    0 0 0.5em black,
    0 0 1em red;
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

## `backdrop-filter`

Aplica un efecto visual (difuminado, brillo, contraste, etc.) sobre lo que se ve **detrás** de un elemento, en vez de sobre el elemento mismo.

```css
.card {
    background-color: rgba(255, 255, 255, 0.7);
    backdrop-filter: blur(6px);
}
```

Es el efecto conocido como "vidrio esmerilado" (frosted glass): el fondo detrás de la caja se ve difuminado a través de ella, mientras el contenido de la caja permanece nítido. Suele combinarse con un fondo semitransparente (con `rgba` u `opacity`) para que el efecto de difuminado sea visible.

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
| ---------- | ------------------------: | ----------------------------- | ----------------------: |
| `static`   |                        Sí | Flujo normal                  |                      Sí |
| `relative` |                        Sí | Su posición original          |                      Sí |
| `absolute` |                        No | Ancestro posicionado          |                      Sí |
| `fixed`    |                        No | Viewport                      |                      No |
| `sticky`   |                        Sí | Contenedor y límite indicado  |            Parcialmente |

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

# Flexbox

Flexbox es un modelo de diseño (`display: flex`) pensado para distribuir elementos dentro de un contenedor de forma flexible y adaptable a distintos tamaños de pantalla.

Surge principalmente para facilitar la maquetación responsiva, en especial en dispositivos móviles: al aplicar `display: flex`, los elementos hijos pasan a acomodarse uno al lado del otro de forma flexible, en vez de apilarse como cajas de bloque.

## Activar flexbox

```css
.container {
    display: flex;
}
```

Al aplicar `display: flex` a un contenedor, todos sus hijos directos (llamados **flex items**) se acomodan automáticamente en una fila, uno al lado del otro.

## Ejes de flexbox

Flexbox trabaja siempre con dos ejes:

```text
main axis  → eje principal
cross axis → eje secundario, perpendicular al principal
```

Por defecto (con `flex-direction: row`):

```text
main axis  → va de izquierda a derecha
cross axis → va de arriba hacia abajo
```

```text
                main axis ─────────────────────►
              ┌───────────────────────────────────┐
              │ ┌────┐   ┌────┐   ┌────┐           │
cross axis    │ │ 1  │   │ 2  │   │ 3  │           │
    │         │ └────┘   └────┘   └────┘           │
    ▼         └───────────────────────────────────┘
```

## `flex-direction`

Define la dirección del main axis.

```css
flex-direction: row;
```

Valores:

```text
row            → izquierda a derecha (por defecto)
row-reverse    → derecha a izquierda
column         → arriba hacia abajo
column-reverse → abajo hacia arriba
```

Cuando `flex-direction` es `column` o `column-reverse`, los ejes se invierten: el main axis pasa a ser vertical y el cross axis horizontal.

```text
row (por defecto)             column
main axis ───────►            main axis
┌───┐ ┌───┐ ┌───┐              │
│ 1 │ │ 2 │ │ 3 │              ▼
└───┘ └───┘ └───┘             ┌───┐
                               │ 1 │
                               ├───┤
                               │ 2 │
                               ├───┤
                               │ 3 │
                               └───┘
```

## `flex-wrap`

Define si los elementos deben mantenerse en una sola línea o pueden pasar a otra cuando no caben en el contenedor.

```css
flex-wrap: wrap;
```

Valores:

```text
nowrap       → todos los elementos permanecen en una sola línea (por defecto)
wrap         → los elementos pasan a nuevas líneas cuando no caben
wrap-reverse → igual que wrap, pero las líneas se acomodan en orden inverso
```

Sin `flex-wrap: wrap`, los elementos se encogen o desbordan el contenedor para mantenerse en una sola línea.

```text
nowrap                              wrap
┌───────────────────────┐           ┌───────────────────────┐
│┌──┐┌──┐┌──┐┌──┐┌──┐┌──┐│           │┌──┐┌──┐┌──┐┌──┐       │
││1 ││2 ││3 ││4 ││5 ││6 ││           ││1 ││2 ││3 ││4 │       │
│└──┘└──┘└──┘└──┘└──┘└──┘│           │└──┘└──┘└──┘└──┘       │
└───────────────────────┘           │┌──┐┌──┐               │
(se encogen para entrar)            ││5 ││6 │               │
                                     │└──┘└──┘               │
                                     └───────────────────────┘
                                     (pasan a una nueva línea)
```

## `justify-content`

Alinea los elementos a lo largo del **main axis**.

```css
justify-content: center;
```

Valores frecuentes:

```text
flex-start    → agrupa los elementos al inicio del main axis (por defecto)
flex-end      → agrupa los elementos al final del main axis
center        → agrupa los elementos al centro
space-between → reparte el espacio sobrante entre los elementos, sin espacio en los extremos
space-around  → reparte el espacio sobrante alrededor de cada elemento
space-evenly  → reparte el espacio sobrante de forma equitativa en todos los lados
```

```text
flex-start:     [1][2][3]

center:              [1][2][3]

flex-end:                 [1][2][3]

space-between:  [1]      [2]      [3]

space-evenly:      [1]    [2]    [3]
```

## `align-items`

Alinea los elementos a lo largo del **cross axis**, dentro de una misma línea.

```css
align-items: center;
```

Valores frecuentes:

```text
stretch    → estira los elementos para ocupar todo el cross axis (valor por defecto)
flex-start → los alinea al inicio del cross axis
flex-end   → los alinea al final del cross axis
center     → los alinea al centro del cross axis
baseline   → los alinea según la línea base del texto
```

## `align-content`

Alinea las **líneas** de elementos a lo largo del cross axis, cuando hay más de una línea. Requiere `flex-wrap: wrap` (sin líneas múltiples, no tiene efecto).

```css
align-content: space-between;
```

Es equivalente a `justify-content`, pero aplicado al cross axis y agrupando líneas completas en vez de elementos individuales.

Valores frecuentes:

```text
flex-start   → agrupa las líneas al inicio
flex-end     → agrupa las líneas al final
center       → agrupa las líneas al centro
stretch      → estira las líneas para ocupar el espacio disponible (sin valor por defecto fijo)
space-around → da espacio alrededor de cada línea (el espacio entre líneas se suma)
space-evenly → da espacio equitativo entre todas las líneas
```

## Propiedades de los flex items

Las siguientes propiedades se aplican a los **hijos** de un contenedor flex, no al contenedor.

### `flex-grow`

Define cuánto puede **crecer** un elemento para ocupar el espacio sobrante del contenedor.

```css
flex-grow: 2;
```

El valor por defecto es `0` (los elementos no crecen). Cuando varios elementos declaran `flex-grow`, el espacio sobrante se reparte proporcionalmente entre ellos según su valor.

### `flex-shrink`

Define cuánto puede **encogerse** un elemento cuando falta espacio en el contenedor.

```css
flex-shrink: 1;
```

Funciona de forma similar a `flex-grow`, pero en sentido contrario: en vez de repartir el espacio sobrante, reparte el espacio faltante entre los elementos. Gracias a `flex-grow` y `flex-shrink` los elementos son "flexibles".

### `flex-basis`

Define el tamaño base de un elemento en el main axis, antes de aplicar `flex-grow` o `flex-shrink`.

```css
flex-basis: auto;
```

Su comportamiento depende de `flex-direction`: si el main axis es horizontal (`row`), se comporta como un `width`; si es vertical (`column`), se comporta como un `height`.

`flex-grow`, `flex-shrink` y `flex-basis` suelen combinarse mediante el shorthand `flex`:

```css
flex: 1 1 auto;
```

```text
flex-grow: 1
flex-shrink: 1
flex-basis: auto
```

### `order`

Define el orden en el que aparece un elemento dentro del contenedor, sin modificar el HTML.

```css
.elemento {
    order: 1;
}
```

Por defecto, todos los elementos tienen `order: 0` y se acomodan en el orden en que aparecen en el HTML. Los elementos se ordenan de menor a mayor según su valor de `order`.

### `align-self`

Sobrescribe el valor de `align-items` para un elemento en particular.

```css
.elemento {
    align-self: center;
}
```

Alinea el elemento a través del cross axis, igual que `align-items`, pero se aplica únicamente al elemento donde se declara. Acepta los mismos valores (`stretch`, `flex-start`, `flex-end`, `center`, `baseline`).

## Comparación de propiedades del contenedor

| Propiedad         | Eje que afecta | Qué alinea                          |
| ------------------ | --------------- | ------------------------------------ |
| `justify-content`  | main axis        | elementos dentro de una línea        |
| `align-items`      | cross axis       | elementos dentro de una línea        |
| `align-content`    | cross axis       | líneas completas (requiere `wrap`)   |

---

# Variables CSS (Custom Properties)

Las variables en CSS se llaman formalmente **custom properties** (propiedades personalizadas). Permiten guardar un valor y reutilizarlo en distintos lugares de una hoja de estilos.

## Declarar una variable

Se declaran con dos guiones al inicio del nombre (`--`), dentro de un selector.

```css
:root {
    --border-colores: 1px solid green;
    --color-principal: white;
}
```

`:root` es una pseudoclase que representa el elemento raíz del documento (equivalente a `html`, pero con una especificidad de `10`).

Declarar las variables ahí las hace disponibles para todo el documento, ya que todos los elementos son descendientes de `:root`.

## Usar una variable

Se utilizan mediante la función `var()`.

```css
.title {
    border: var(--border-colores);
}
```

## Valor alternativo (fallback)

`var()` acepta un segundo argumento: un valor alternativo que se usa si la variable indicada no existe o no está definida.

```css
border: var(--border-colores, 2px solid green);
```

## Alcance de las variables

Una variable puede declararse dentro de cualquier selector, no solo en `:root`.

```css
.card {
    --border-colores: 1px solid red;
}
```

Declararla dentro de un selector específico limita su alcance: solo estará disponible para ese elemento y sus elementos descendientes (hijos).

```text
:root     → alcance global, disponible en todo el documento
.selector → alcance local, solo el elemento donde se declara y sus hijos
```

## Ventaja principal

Permiten cambiar un valor (un color, un borde, un espaciado) en un único lugar, y que el cambio se refleje automáticamente en todos los sitios donde se usa la variable.

---

# Grid

`display: grid` crea un sistema de maquetación **bidireccional**: a diferencia de flexbox, que ordena los elementos en una sola dirección a la vez (fila o columna), grid permite controlar filas y columnas al mismo tiempo.

## Conceptos básicos

```text
grid line  → cada una de las líneas que forman la cuadrícula (de columna o de fila)
grid track → el espacio entre dos líneas consecutivas (una columna o una fila)
grid cell  → la intersección entre una fila y una columna
grid area  → un grupo rectangular de una o más celdas
```

## Activar grid

```css
.container {
    display: grid;
}
```

## `grid-template-columns` y `grid-template-rows`

Definen la cantidad y el tamaño de las columnas y filas.

```css
.container {
    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: repeat(5, 1fr);
}
```

`repeat(veces, valor)` es una función que repite un valor una cantidad determinada de veces. En el ejemplo, crea 5 columnas (o 5 filas) iguales.

### Unidad `fr`

`fr` (fracción) reparte el espacio disponible del contenedor en partes iguales.

```css
grid-template-columns: 1fr 1fr 1fr;
```

```text
Contenedor: 900px
3 columnas de 1fr

900px ÷ 3 = 300px cada columna
```

## `gap`

Define el espacio entre filas y columnas.

```css
gap: 10px;
```

También puede controlarse por separado:

```css
column-gap: 20px;
row-gap: 10px;
```

`gap` es similar a `margin`, pero no le resta tamaño a los elementos ni requiere ajustar `top` o `left` para compensar: actúa únicamente en los espacios internos entre celdas.

## Columnas y filas adaptables sin media queries

Combinar `repeat(auto-fit, ...)` con `minmax(min, max)` permite que la cantidad de columnas se ajuste automáticamente según el espacio disponible, sin necesidad de escribir media queries.

```css
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
```

```text
auto-fit           → ajusta la cantidad de columnas al espacio disponible
minmax(250px, 1fr) → cada columna mide al menos 250px, y como máximo
                      reparte el espacio sobrante en partes iguales (1fr)
```

Como `fr` reparte el espacio en partes iguales, todas las columnas mantienen el mismo tamaño entre sí.

## `grid-auto-rows`

Define el tamaño de las filas que se generan automáticamente, cuando no fueron declaradas explícitamente con `grid-template-rows`.

```css
grid-auto-rows: auto;
```

## Ubicar elementos por líneas: `grid-column` y `grid-row`

Cada línea de la cuadrícula tiene un número, empezando en `1`.

```css
.item1 {
    grid-column: 1 / 4;
    grid-row: 1 / 3;
}
```

```text
grid-column: 1 / 4
→ empieza en la línea 1 de columna y termina en la línea 4
  (ocupa las columnas 1, 2 y 3)

grid-row: 1 / 3
→ empieza en la línea 1 de fila y termina en la línea 3
  (ocupa la fila 1 y la fila 2)
```

## Ubicar elementos con nombre: `grid-template-areas` y `grid-area`

Otra forma de ubicar los elementos es nombrando áreas dentro del contenedor.

```css
.container {
    grid-template-areas:
        "nav nav nav nav nav"
        "main main main side side"
        "main main main side side"
        "main main main side side"
        "footer footer footer footer footer";
}
```

Cada línea entre comillas representa una fila de la cuadrícula, y cada palabra representa la columna que ocupa esa celda. Repetir el mismo nombre en celdas contiguas hace que formen una sola área.

Luego, en cada elemento se indica a qué área pertenece:

```css
.item1 {
    grid-area: nav;
}

.item2 {
    grid-area: main;
}

.item3 {
    grid-area: footer;
}

.item4 {
    grid-area: side;
}
```

La cantidad de columnas y filas escritas en `grid-template-areas` debe coincidir con las definidas en `grid-template-columns` y `grid-template-rows`.

Para dejar una celda vacía se usa un punto (`.`) en su lugar.

Un `grid-area` debe formar siempre un rectángulo o un cuadrado; no puede tener forma irregular.

### Diagrama de líneas y áreas

Con 5 columnas y 5 filas, la cuadrícula tiene 6 líneas de columna y 6 líneas de fila (una línea más que la cantidad de columnas o filas, porque las líneas marcan los bordes de cada track).

```text
        1         2         3         4         5         6
      1 ┌─────────┬─────────┬─────────┬─────────┬─────────┐
        │                    nav                          │
      2 ├─────────┬─────────┬─────────┼─────────┬─────────┤
        │                   │                   │         │
      3 │        main       │        side       │         │
        │                   │                   │         │
      4 │                   │                   │         │
        │                   │                   │         │
      5 ├─────────┬─────────┼─────────┴─────────┴─────────┤
        │                   footer                        │
      6 └─────────┴─────────┴─────────┴─────────┴─────────┘
```

```text
nav    → grid-row: 1 / 2   | grid-column: 1 / 6
main   → grid-row: 2 / 5   | grid-column: 1 / 4
side   → grid-row: 2 / 5   | grid-column: 4 / 6
footer → grid-row: 5 / 6   | grid-column: 1 / 6
```

Este resultado es el mismo que se logra con `grid-template-areas`, pero indicando la posición mediante números de línea en vez de nombres.

## Comparación de las dos formas de ubicar elementos

| Método                              | Ventaja                                                        |
| ------------------------------------ | ---------------------------------------------------------------- |
| `grid-column` / `grid-row`           | Útil para posiciones puntuales basadas en números de línea       |
| `grid-template-areas` + `grid-area`  | Más visual y legible; el diseño se puede leer directamente en el CSS |

## `grid-auto-flow`

Define en qué dirección se van acomodando los elementos que no tienen una posición explícita (sin `grid-area`, `grid-column` ni `grid-row`).

```css
.container {
    display: grid;
    grid-auto-flow: column;
}
```

```text
row (por defecto) → acomoda los elementos llenando primero las filas
column            → acomoda los elementos llenando primero las columnas
```

Es útil, por ejemplo, para una lista de enlaces de navegación: con `grid-auto-flow: column`, cada elemento pasa a ocupar una columna nueva en vez de amontonarse en la misma fila.

```css
.nav-list {
    display: grid;
    grid-auto-flow: column;
    gap: 1em;
}
```

## `justify-self` y `align-self` en grid

Así como `align-self` (ya visto en [Flexbox](#flexbox)) sobrescribe la alineación de un elemento en el cross axis, en grid existen dos propiedades equivalentes para un elemento individual dentro de su celda:

```css
.item {
    justify-self: end;
    align-self: end;
}
```

```text
justify-self → alinea el elemento horizontalmente dentro de su celda
align-self   → alinea el elemento verticalmente dentro de su celda
```

Ambas aceptan los valores `start`, `end`, `center` y `stretch` (por defecto). También existen sus versiones para todos los elementos del contenedor a la vez: `justify-items` y `align-items`.

---

# Media Queries

Los media queries permiten aplicar estilos distintos según las características del dispositivo, principalmente el ancho del viewport. Se usan para adaptar el diseño a distintos tamaños de pantalla: celulares, tablets, notebooks.

## Sintaxis

```css
@media (condición) {
    selector {
        propiedad: valor;
    }
}
```

## `max-width` y `min-width`

```css
@media (max-width: 700px) {
    .element {
        background-color: aqua;
    }
}
```

```text
max-width → el bloque se aplica mientras el viewport sea igual o menor a ese ancho
min-width → el bloque se aplica mientras el viewport sea igual o mayor a ese ancho
```

## Orden de los media queries

Por la cascada de CSS, ante una misma especificidad, el navegador aplica la última regla que coincide en el orden en que fue escrita. Por eso el orden de los media queries importa.

```css
.element {
    background-color: moccasin;
}

@media (max-width: 700px) {
    .element {
        background-color: aqua;
    }
}

@media (max-width: 500px) {
    .element {
        background-color: brown;
    }
}
```

```text
Viewport > 700px  → moccasin (regla base, ningún media query aplica)
Viewport ≤ 700px  → aqua (coincide el primer media query)
Viewport ≤ 500px  → coinciden aqua y brown a la vez, pero se aplica brown
                     por ser la última declaración en el código
```

Al trabajar con `max-width`, conviene escribir los media queries de mayor a menor ancho, para que el breakpoint más chico (más específico) quede al final y pueda sobrescribir a los anteriores.

Por esta misma razón, los media queries suelen ubicarse al final del archivo CSS: así se aseguran de sobrescribir las reglas base que ya fueron declaradas más arriba.

## No se limitan a una sola clase

Un media query puede afectar a cualquier selector dentro de su bloque, no solo a la clase que se esté adaptando.

```css
@media (min-width: 500px) {
    body {
        background-color: antiquewhite;
    }
}
```

---

# Transform

`transform` permite mover, rotar, escalar o inclinar un elemento, sin afectar el flujo normal del documento ni la posición de otros elementos.

```css
.element {
    transform: translateX(100px);
}
```

El navegador trabaja con un eje `x` y un eje `y`:

```text
x: positivo → hacia la derecha | negativo → hacia la izquierda
y: positivo → hacia abajo      | negativo → hacia arriba
```

## `translate`

Desplaza un elemento desde su posición original, sin modificar la posición de otros elementos (a diferencia de, por ejemplo, cambiar un `margin`).

```css
transform: translateX(100px); /* 100px a la derecha */
transform: translateY(50px);  /* 50px hacia abajo */
```

Si se usan porcentajes, se calculan sobre el propio tamaño del elemento (no sobre el contenedor):

```text
Elemento: 300px de ancho
translateX(100%) → se desplaza 300px (el 100% de su propio ancho)
```

Para aplicar ambos ejes a la vez, deben ir en la misma línea. Por la cascada, si se repite la propiedad `transform`, solo se aplica la última declaración completa:

```css
transform: translateX(100px) translateY(50px);
```

Forma abreviada (shorthand), con el eje `x` primero y el `y` después:

```css
transform: translate(100px, 50px);
```

## `rotate`

Rota un elemento. Solo acepta valores angulares:

```css
transform: rotate(45deg);
```

```text
deg  → grados, de 0deg a 360deg
grad → gradianes, de 0 a 400grad
rad  → radianes, de 0 a 6.28rad
turn → vueltas completas, de 0 a 1turn
```

## `scale`

Escala el tamaño de un elemento. Toma un valor numérico (sin unidad).

```css
transform: scale(1.5);
```

```text
scale(1)   → 100% (tamaño original)
scale(2)   → 200%
valor > 1  → aumenta el tamaño
valor < 1  → disminuye el tamaño
```

También existen `scaleX` y `scaleY` para escalar un solo eje, y una forma abreviada con ambos ejes:

```css
transform: scale(2, 1); /* eje x al doble, eje y sin cambios */
```

## `skew`

Inclina un elemento (y su contenido, incluido el texto).

```css
transform: skewX(10deg);
transform: skewY(10deg);
```

No se recomienda usar `skew` de forma aislada, ya que puede generar diferencias de compatibilidad entre navegadores.

## `transform-origin`

Define el punto desde el cual se aplican las transformaciones (el "pivote"). Por defecto, ese punto es el centro del elemento (`50% 50%`).

```css
.form__label {
    transform: translateY(-12px) scale(0.7);
    transform-origin: top left;
}
```

```text
center (por defecto) → rota/escala desde el centro del elemento
top left             → rota/escala desde la esquina superior izquierda
bottom right         → rota/escala desde la esquina inferior derecha
```

Es especialmente importante para `scale` y `rotate`: cambiar el `transform-origin` cambia hacia dónde "crece" o hacia dónde gira el elemento. Por ejemplo, con `scale`, si el origen es `top left`, el elemento se achica o agranda manteniendo fija su esquina superior izquierda, en vez de mantener fijo su centro.

## Combinar varios valores

Un `transform` puede combinar varias funciones en una misma declaración.

```css
transform: translateX(100px) rotate(45deg) scale(1.5);
```

El orden de los valores importa: cada función se aplica sobre el resultado de la anterior, por lo que escalar y luego rotar no da el mismo resultado que rotar y luego escalar.

## Por qué usar `transform`

`transform` consume menos recursos que animar `width` o `height`, porque el navegador no necesita recalcular el layout de toda la página: el cambio se aplica únicamente sobre el elemento, en una capa aparte.

---

# Transiciones

Una transición es un cambio de valor de una propiedad CSS de forma suave (gradual en el tiempo), en vez de un cambio instantáneo. Se activan cuando esa propiedad cambia de valor, por ejemplo al aplicarse una pseudoclase como `:hover`.

No todas las propiedades CSS pueden animarse mediante transiciones.

## Propiedades de transition

```css
.element {
    transition-property: all;
    transition-duration: 1s;
}
```

### `transition-property`

Especifica qué propiedad se va a animar.

```css
transition-property: background-color;
```

El valor por defecto es `all` (anima cualquier propiedad que cambie), pero no conviene dejarlo así: `all` consume más recursos, porque el navegador debe vigilar todas las propiedades por si cambian. Es preferible especificar la propiedad concreta, como `background-color` o `transform`.

### `transition-duration`

Especifica cuánto dura la animación.

```css
transition-duration: 1s;
```

Por defecto es `0s` (sin transición, el cambio es instantáneo).

### `transition-timing-function`

Especifica la curva de aceleración de la transición.

```css
transition-timing-function: ease;
```

```text
ease        → empieza lento, se acelera, y termina lento (valor por defecto)
linear      → velocidad constante, sin cambios
ease-in     → empieza lento y termina rápido
ease-out    → empieza rápido y termina lento
ease-in-out → empieza lento, se acelera, y termina lento (más marcado que ease)
step-start  → el cambio ocurre de golpe, al inicio
step-end    → el cambio ocurre de golpe, al final
```

### `transition-delay`

Especifica cuánto tiempo tarda en iniciar la transición, una vez que la propiedad cambia de valor.

```css
transition-delay: 0.5s;
```

Por defecto es `0s`.

## Shorthand `transition`

```css
transition: background-color 1s ease 0.5s;
```

```text
transition: property duration timing-function delay;
```

El único valor obligatorio es `duration`; el resto tiene valores por defecto.

## Ejemplo: animar según el hover de un contenedor

```css
.element {
    transition-property: all;
    transition-duration: 1s;
}

.container:hover .element {
    transform: translateX(240px) rotate(360deg) scale(1);
}
```

Aplicar el `transform` cuando el **contenedor** recibe `:hover` (en vez de aplicarlo directamente al elemento animado) evita que la animación se interrumpa: si el `:hover` estuviera en `.element`, el mouse podría "salirse" del elemento a medida que este se mueve, cortando la animación a mitad de camino.

---

# Animaciones

Una animación en CSS permite definir una secuencia de estados (no solo un punto de inicio y uno final, como una transición) mediante la regla `@keyframes`.

## `@keyframes`

Define el nombre de la animación y los valores que toman las propiedades en distintos momentos.

```css
@keyframes mover {
    0% {
        transform: translateX(0px);
        background-color: tomato;
    }
    50% {
        transform: translateX(240px) rotate(360deg);
    }
    100% {
        transform: translate(0, 0);
        background-color: darkgoldenrod;
    }
}
```

Los porcentajes representan el progreso de la animación, del `0%` (inicio) al `100%` (final). También pueden agregarse pasos intermedios, como `25%` o `75%`.

Cuando solo hay dos estados (inicio y final), puede usarse `from` y `to` en vez de porcentajes:

```css
@keyframes cambiar-color {
    from {
        background-color: darkgoldenrod;
    }
    to {
        background-color: darkorange;
    }
}
```

## Aplicar la animación a un elemento

```css
.element {
    animation-name: mover;
    animation-duration: 2s;
    animation-timing-function: ease;
    animation-iteration-count: 3;
    animation-direction: alternate;
    animation-fill-mode: forwards;
}
```

### `animation-name`

Indica qué `@keyframes` se va a usar.

```css
animation-name: mover;
```

### `animation-duration`

Especifica cuánto dura un ciclo completo de la animación.

```css
animation-duration: 2s;
```

### `animation-timing-function`

Especifica la curva de aceleración de la animación. Acepta los mismos valores que `transition-timing-function` (`ease` por defecto, `linear`, `ease-in`, `ease-out`, `ease-in-out`, `step-start`, `step-end`).

### `animation-iteration-count`

Especifica cuántas veces se repite la animación.

```css
animation-iteration-count: 3;
animation-iteration-count: infinite;
```

Por defecto es `1`.

### `animation-direction`

Especifica en qué sentido avanza la animación en cada repetición.

```text
normal            → siempre de 0% a 100% (valor por defecto)
reverse           → siempre de 100% a 0%
alternate         → alterna: primero 0% → 100%, luego 100% → 0%, y así sucesivamente
alternate-reverse → alterna, pero empezando de 100% → 0%
```

`alternate` se usa para que la animación vuelva al estado inicial de forma suave (recorriendo los mismos pasos hacia atrás), en vez de saltar de golpe del `100%` al `0%` al reiniciar.

### `animation-delay`

Especifica cuánto tiempo tarda en iniciar la animación.

```css
animation-delay: 0.5s;
```

Por defecto es `0s`.

### `animation-fill-mode`

Especifica qué estilos se aplican antes de que empiece la animación y después de que termina.

```text
none      → no aplica ningún estilo del @keyframes fuera de cuando la animación está corriendo (valor por defecto)
forwards  → al terminar, mantiene los estilos del último keyframe (100%, o el que corresponda según la dirección)
backwards → antes de empezar (por ejemplo, durante un animation-delay), aplica los estilos del primer keyframe
both      → combina forwards y backwards
```

### `animation-play-state`

Permite pausar o reanudar una animación en curso.

```css
.element:hover {
    animation-play-state: paused;
}
```

En este ejemplo, la animación se pausa mientras el cursor esté sobre el elemento.

## Shorthand `animation`

```css
animation: mover 2s ease 0s 3 alternate forwards;
```

```text
animation: name duration timing-function delay iteration-count direction fill-mode;
```

---

# Metodología BEM

BEM significa **Block, Element, Modifier**. Es una convención para nombrar clases de CSS de forma clara y consistente, pensada para mantener el código flexible, modular y fácil de mantener a medida que un proyecto crece.

No es una propiedad ni una regla de CSS: es una forma de organizar los nombres de las clases en el HTML y el CSS.

## Block (bloque)

Es una parte independiente de la interfaz, que no necesita de otros elementos para funcionar por sí misma.

Su nombre describe qué representa, no cómo se ve:

```css
.header { }
.menu { }
.footer { }
```

## Element (elemento)

Es una parte de un block que no puede existir por sí sola; siempre pertenece a un block.

Se nombra como `block__element` (dos guiones bajos):

```css
.header__title { }
.menu__item { }
.footer__copyright { }
```

## Modifier (modificador)

Es un estado o una variación de un block o de un element: por ejemplo, un color distinto, un tamaño distinto, o un estado como "activo" o "deshabilitado".

Se nombra como `block--modificador` o `block__element--modificador` (dos guiones):

```css
.header--dark { }
.menu__item--active { }
.footer__copyright--small { }
```

## Resumen de la nomenclatura

```text
.block                    → parte independiente de la interfaz
.block__element           → parte de un block, no existe por sí sola
.block--modifier          → variación o estado de un block
.block__element--modifier → variación o estado de un element
```

```text
__  (dos guiones bajos) → separa el block de su element
--  (dos guiones)       → separa el block/element de su modifier
```

## Ejemplo

```html
<div class="card card--featured">
    <img class="card__image" />
    <h2 class="card__title">Título</h2>
    <p class="card__paragraph card__paragraph--muted">Texto</p>
</div>
```

```text
.card                    → el block
.card--featured          → una variación del block (por ejemplo, destacada)
.card__image              → un element del block
.card__title              → otro element del block
.card__paragraph          → otro element del block
.card__paragraph--muted   → una variación de ese element (por ejemplo, texto atenuado)
```

BEM evita depender de la jerarquía del HTML para aplicar estilos (por ejemplo, `.card h2`), y en cambio nombra cada parte de forma explícita. Esto hace que el CSS sea más fácil de reutilizar y de entender, incluso sin ver el HTML.

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

---

# Ejemplo práctico: card (bordes y sombras)

```css
* {
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Courier New', Courier, monospace;
}

.card {
    max-width: 350px;
    margin: 80px auto;
    box-shadow: 0 0 3px;
    border-radius: 1em;
}

.card-img {
    width: 100%;
    display: block;
    border-radius: 1em 1em 0 0;
}

.card-container {
    color: white;
    background-color: rgb(35, 0, 35);
    border-radius: 0 0 1em 1em;
    padding: 40px 15px;
    text-align: center;
}

.card-title {
    margin-bottom: 15px;
}

.card-paragraph {
    line-height: 1.5;
    text-align: start;
}

.card-button {
    display: inline-block;
    background-color: rgb(151, 141, 0);
    text-decoration: none;
    color: white;
    padding: 1em 2em;
    margin-top: 1em;
    border-radius: 2em;
}
```

En este ejemplo se combinan conceptos ya vistos (`max-width`, `margin: auto`, `display: inline-block`, `line-height`, `text-align`) con dos propiedades nuevas:

* `box-shadow: 0 0 3px` en `.card` da una sombra suave alrededor de toda la tarjeta, sin necesidad de un borde visible.
* `border-radius` redondea las esquinas de `.card`, `.card-img` (solo arriba, para que la imagen quede pegada al contenedor de texto) y `.card-container` (solo abajo). En `.card-button`, un `border-radius` grande (`2em`) genera un botón con forma de píldora.

---

# Ejemplo práctico: flexbox

```css
* {
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

.flex {
    width: 90%;
    max-width: 800px;
    min-height: 600px;
    margin: 80px auto;
    border: 3px solid black;
    display: flex;
    flex-wrap: wrap;
    outline: 3px solid black;
}

.element {
    color: #fff;
    font-size: 2rem;
    text-align: center;
    line-height: 100px;
    width: 100px;
    height: 100px;
}

.element1 {
    background-color: red;
}

.element2 {
    background-color: green;
}

.element3 {
    background-color: blue;
    align-self: center;
}
```

En este ejemplo:

* `.flex` es el contenedor flex (`display: flex`), con `flex-wrap: wrap` para permitir que los elementos pasen a nuevas líneas si no caben.
* `.element1`, `.element2` y `.element3` son los flex items.
* `.element3` usa `align-self: center` para alinearse distinto a sus hermanos dentro del cross axis, sin necesidad de cambiar `align-items` en el contenedor.
* El `outline` en `.flex` es solo una guía visual: al no formar parte del box model, no afecta el tamaño del contenedor ni la distribución de los elementos internos.

Este código práctico también incluye, comentadas, las propiedades `justify-content`, `align-items`, `align-content`, `flex-grow`, `flex-shrink`, `flex-basis` y `order` para ir probándolas una por una (ver el archivo `flexbox.css` con los comentarios corregidos).

---

# Ejemplo práctico: variables CSS

```css
:root {
    --border-colores: 1px solid green;
    --color-principal: white;
}

* {
    box-sizing: border-box;
}

body {
    font-family: 'Courier New', Courier, monospace;
}

.title {
    border: var(--border-colores);
    color: darkgoldenrod;
}

.btn {
    display: inline-block;
    padding: 15px 30px;
    background-color: rgb(17, 1, 13);
    color: var(--color-principal);
    text-decoration: none;
}

.paragraph {
    color: var(--color-principal);
}
```

En este ejemplo, `--border-colores` y `--color-principal` se declaran en `:root`, por lo que están disponibles en todo el documento. `.title` usa `var(--border-colores)` para su borde, y tanto `.btn` como `.paragraph` reutilizan `var(--color-principal)` para el color de texto. Si se necesita cambiar el color principal del sitio, alcanza con modificar una sola línea dentro de `:root`.

> Nota: en el original, `--color-principal` se había declarado como `--color-principal: color: white;`. Una custom property guarda directamente un **valor**, no una declaración completa (no lleva el nombre de la propiedad adentro), por eso se corrigió a `--color-principal: white;`.

---

# Ejemplo práctico: grid

```css
* {
    color: white;
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Courier New', Courier, monospace;
}

.container {
    width: 90%;
    height: 600px;
    border: 2px solid black;
    margin: 80px auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 10px;
    grid-template-areas:
        "nav nav nav nav nav"
        "main main main side side"
        "main main main side side"
        "main main main side side"
        "footer footer footer footer footer";
}

.item {
    font-size: 2em;
    display: flex;
    align-items: center;
    justify-content: center;
}

.item1 {
    background-color: rgb(84, 17, 17);
    grid-area: nav;
}

.item2 {
    background-color: rgb(6, 6, 109);
    grid-area: main;
}

.item3 {
    background-color: rgb(16, 56, 16);
    grid-area: footer;
}

.item4 {
    background-color: rgb(67, 47, 21);
    grid-area: side;
}

.item5 {
    background-color: darkslategray;
}
```

En este ejemplo, `.container` es el contenedor grid, y las cinco áreas (`nav`, `main`, `main`, `side`, `footer`) se definen con `grid-template-areas`. Cada `.item` se asigna a su área mediante `grid-area`. Además, cada `.item` es a la vez un contenedor flex (`display: flex`) para centrar su contenido, lo que muestra que grid y flexbox pueden combinarse: grid ordena la estructura general de la página, y flexbox el contenido interno de cada celda.

Este código también incluye, comentadas, las alternativas con `grid-column` y `grid-row` (posicionamiento por número de línea) para comparar ambos métodos (ver el archivo `grid.css` con los comentarios corregidos).

---

# Ejemplo práctico: media queries

```css
* {
    margin: 0;
}

body {
    background-color: blueviolet;
}

.element {
    background-color: moccasin;
    width: 300px;
    height: 300px;
    margin: 30px auto;
}

@media (max-width: 700px) {
    .element {
        background-color: aqua;
    }
}

@media (max-width: 500px) {
    .element {
        background-color: brown;
    }
}

@media (min-width: 500px) {
    body {
        background-color: antiquewhite;
    }
}
```

En este ejemplo:

* `.element` empieza con fondo `moccasin`.
* Por debajo de `700px` de ancho de viewport, pasa a `aqua`.
* Por debajo de `500px`, pasa a `brown` (esta regla gana porque está escrita después que la de `700px`, y ambas coinciden a la vez en ese rango).
* A partir de `500px` de ancho (`min-width: 500px`), el fondo del `body` cambia a `antiquewhite`.

---

# Ejemplo práctico: selectores, pseudoclases y pseudoelementos

```css
* {
    box-sizing: border-box;
    margin: 0;
}

body {
    font-family: Arial, Helvetica, sans-serif;
}

.button {
    margin: 50px;
    display: block;
    color: white;
    text-decoration: none;
    padding: 20px 0;
    text-align: center;
    width: 200px;
}

.btn-red + .btn-purple {
    background-color: blue;
}

.btn-red {
    background-color: red;
}

.btn-red:hover {
    transform: scale(1.2);
}

.btn-purple {
    background-color: purple;
}

.btn-purple:active {
    transform: scale(1.2);
}

.btn-tomato {
    background-color: tomato;
}

.btn-red * {
    background-color: green;
}

.element {
    width: max-content;
    padding: 20px;
    color: white;
    font-size: 30px;
    margin: 60px;
    background-color: darkgoldenrod;
    margin-left: 40px;
}

.input {
    display: block;
    margin: 20px;
    padding: 16px;
    font-size: inherit;
    font-family: inherit;
}

.input:focus {
    border: 2px solid blue;
}

.label {
    background-color: red;
    color: white;
}

.check {
    display: inline-block;
    margin-top: 20px;
    margin-bottom: 20px;
    margin-left: 20px;
}

.check:checked + .label {
    background-color: green;
    transform: scale(1.2);
}

.element::after {
    content: "";
}
```

En este ejemplo:

* `.btn-red + .btn-purple` es un selector de hermano adyacente: solo afecta a `.btn-purple` cuando aparece justo después de `.btn-red` en el HTML.
* `.btn-red *` selecciona a todos los descendientes de `.btn-red`.
* `.btn-red:hover` y `.btn-purple:active` cambian de tamaño según el estado del mouse.
* `.input:focus` resalta el borde cuando el input está activo.
* `.check:checked + .label` cambia el estilo de la etiqueta cuando el checkbox asociado está marcado.
* `.element::after` crea un pseudoelemento vacío (requiere `content: ""` para existir, aunque no se le haya dado tamaño ni contenido visible en este ejemplo puntual).

---

# Ejemplo práctico: transform

```css
* {
    box-sizing: border-box;
    margin: 0;
}

.element {
    width: 300px;
    height: 300px;
    background-color: darkgoldenrod;
    margin: 60px;

    transform: translateX(100px) rotate(45deg) scale(1.2);
}
```

En este ejemplo se combinan las tres funciones de `transform` en una sola declaración: primero desplaza el elemento `100px` a la derecha, luego lo rota `45deg` y por último lo escala al `120%`. Como el orden de las funciones importa, cambiar el orden (por ejemplo, escalar antes de rotar) puede dar un resultado visual distinto.

> Nota: en el código original, la propiedad `transform` se repetía tres veces seguidas (`translateX`, luego `rotate`, luego `scale`) dentro de la misma regla. Por la cascada, solo se aplica la última declaración válida (`transform: scale` sin ningún valor, que además es inválida). Para combinar las tres transformaciones a la vez, deben ir juntas en una sola línea, como en el ejemplo de arriba.

---

# Ejemplo práctico: box-shadow y border-radius

```css
* {
    margin: 0;
    box-sizing: border-box;
}

.element {
    margin: 80px auto;
    width: 200px;
    height: 200px;
    background-color: darkgoldenrod;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 10px 10px 1em;
}

.ojo {
    margin: 1em;
    width: 4em;
    height: 4em;
    background-color: rgb(255, 252, 252);
    border-radius: 50%;
    box-shadow: 0 0 0.5em;
    display: flex;
    justify-content: center;
    align-items: center;
}

.pupila {
    width: 2em;
    height: 2em;
    background-color: rgb(8, 8, 8);
    box-shadow: 0 0 0.5em;
    border-radius: 50%;
}
```

En este ejemplo, `.ojo` y `.pupila` usan `border-radius: 50%` sobre elementos cuadrados para formar dos círculos concéntricos (un "ojo" con su pupila), cada uno con su propia sombra suave (`box-shadow: 0 0 0.5em`, sin desplazamiento, solo difuminado).

---

# Ejemplo práctico: transiciones

```css
* {
    box-sizing: border-box;
    margin: 0;
}

.element {
    width: 300px;
    height: 300px;
    background-color: darkgoldenrod;
    margin: 60px;

    transition-property: all;
    transition-duration: 1s;
}

.container:hover .element {
    transform: translateX(240px) rotate(360deg) scale(1);
}
```

En este ejemplo, `.element` tiene declarada una transición sobre `all`, con una duración de `1s`. El cambio de `transform` se dispara cuando su contenedor (`.container`) recibe `:hover`, no el propio `.element`; así se evita que la animación se corte si el elemento se mueve fuera del alcance del cursor.

---

# Ejemplo práctico: animaciones

```css
* {
    box-sizing: border-box;
    margin: 0;
}

.element {
    width: 300px;
    height: 300px;
    background-color: darkgoldenrod;
    border-radius: 50%;
    margin: 60px;

    animation-name: mover;
    animation-duration: 2s;
    animation-timing-function: ease;
    animation-iteration-count: 3;
    animation-direction: alternate;
    animation-fill-mode: forwards;
}

.element:hover {
    animation-play-state: paused;
}

@keyframes mover {
    0% {
        transform: translateX(0px);
        background-color: tomato;
    }
    25% {
        transform: translateX(240px);
        background-color: darkorange;
    }
    50% {
        transform: translateX(240px) rotate(360deg);
    }
    75% {
        transform: translate(0, 120px);
    }
    100% {
        transform: translate(0, 0);
        background-color: darkgoldenrod;
    }
}

@keyframes cambiar-color {
    from {
        background-color: darkgoldenrod;
    }
    to {
        background-color: darkorange;
    }
}

@keyframes crecer {
    0% {
        transform: scale(1);
    }
    50% {
        transform: scale(2.5);
    }
    100% {
        transform: scale(1);
    }
}
```

En este ejemplo, `.element` usa la animación `mover` (definida con `@keyframes`), que combina desplazamiento, rotación y cambio de color en distintos puntos del recorrido (`0%`, `25%`, `50%`, `75%`, `100%`). Con `animation-direction: alternate`, al llegar al final la animación vuelve sobre sus pasos en vez de saltar de golpe al inicio, y `animation-fill-mode: forwards` mantiene el último estado una vez que se completan las 3 repeticiones (`animation-iteration-count: 3`).

`@keyframes cambiar-color` y `@keyframes crecer` quedan definidas pero sin usarse todavía en ningún selector; se dejan documentadas por si se retoman en una práctica posterior.

---

# Ejemplo práctico: landing page (grid responsive + BEM)

```css
:root {
    --White: hsl(0, 100%, 100%);
    --Grey-500: hsl(0, 0%, 63%);
    --Grey-800: hsl(0, 0%, 27%);
    --Black: hsl(0, 0%, 0%);
}

* {
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: "League Spartan", sans-serif;
}

.container {
    width: 90%;
    margin: 0 auto;
    padding: 60px 0;
}

.main {
    max-width: 1400px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: repeat(5, max-content);
    grid-template-areas:
        "main"
        "buy"
        "image1"
        "about"
        "image2";
}

.main__hero {
    min-height: 500px;
    background-image: url("../images/desktop-image-hero-1.jpg");
    background-size: cover;
    background-position: center;
    grid-area: main;
}

.main__nav {
    display: flex;
}

.main__links {
    display: none;
}

.main__logo {
    margin: 0 auto;
}

.main__controls {
    background-color: black;
    display: flex;
    width: 100px;
    height: 50px;
    justify-content: space-around;
    align-items: center;
    align-self: flex-end;
    justify-self: end;
}

.main__arrows {
    height: 40%;
}

.main__buy {
    grid-area: buy;
}

.main__content {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    flex-direction: column;
}

.main__title {
    color: var(--Black);
}

.main__paragraph {
    line-height: 1.5;
    margin: 1em 0 2em;
    color: var(--Grey-500);
}

.main__paragraph--about {
    margin: 1em 0 0 0;
}

.main__cta {
    text-decoration: none;
    color: var(--Grey-800);
    text-transform: uppercase;
    letter-spacing: 4px;
}

.main__arrow {
    margin-left: 20px;
}

.main__bg {
    grid-area: image1;
    min-height: 250px;
    height: 100%;
    background-image: url("../images/image-about-dark.jpg");
    background-size: cover;
    background-position: center;
}

.main__about {
    grid-area: about;
}

.main__bg--second {
    grid-area: image2;
    background-image: url("../images/image-about-light.jpg");
}

@media (min-width: 768px) {
    .container {
        width: 85%;
        padding: 70px 0;
    }
    .main {
        grid-template-columns: repeat(7, 1fr);
        grid-template-areas:
            "main main main main buy buy buy"
            "main main main main buy buy buy"
            "main main main main buy buy buy"
            "image1 image1 about about about image2 image2";
    }
    .main__controls {
        grid-area: buy;
        justify-self: start;
    }
    .main__hamburguer {
        display: none;
    }
    .main__links {
        padding: 0;
        display: grid;
        grid-auto-flow: column;
        gap: 1em;
        margin-left: 10%;
    }
    .main__list {
        list-style: none;
    }
    .main__link {
        color: var(--White);
        text-decoration: none;
    }
    .main__logo {
        margin: 0px;
    }
}

.attribution {
    color: var(--White);
    background-color: #A16207;
    width: fit-content;
    border-radius: 1em;
    padding: 1em;
    font-size: 0.5em;
    position: fixed;
    z-index: 9999;
    opacity: 0.85;
    bottom: 20px;
    right: 20px;
    font-weight: 500;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.25);
    backdrop-filter: blur(6px);
}

.attribution a {
    display: inline-block;
    font-weight: bold;
    transition: transform 0.2s ease, color 0.2s ease;
    color: rgb(47, 1, 67);
    letter-spacing: normal;
    text-transform: none;
}

.attribution a:hover {
    transform: scale(1.2);
    color: #1E0A45;
}
```

Este ejemplo combina varios temas ya vistos con algunos detalles nuevos:

* **Nomenclatura BEM**: todas las clases siguen el patrón `main__elemento` (`main__hero`, `main__nav`, `main__buy`) y `main__elemento--modificador` (`main__paragraph--about`, `main__bg--second`).
* **Grid responsive sin duplicar el CSS de cada elemento**: el layout mobile usa una sola columna (`grid-template-columns: 1fr`) y se reordena completo a 7 columnas en el media query de `768px`, solo redefiniendo `grid-template-columns` y `grid-template-areas`. Los elementos (`grid-area: main`, `buy`, `image1`, `about`, `image2`) no cambian.
* **`grid-auto-flow: column`** en `.main__links`: hace que cada `<li>` del menú ocupe una columna nueva en vez de apilarse en la misma fila.
* **`justify-self`** en `.main__controls`: alinea ese elemento dentro de su propia celda de grid (a la derecha en mobile, a la izquierda en desktop), sin afectar a los demás elementos del grid.
* **Tamaños intrínsecos**: `grid-template-rows: repeat(5, max-content)` hace que cada fila mida justo lo que necesita su contenido, y `.attribution` usa `width: fit-content` para ajustarse exactamente al texto que contiene.
* **`opacity` + `backdrop-filter`** en `.attribution`: el `opacity: 0.85` vuelve translúcido todo el cartel, y `backdrop-filter: blur(6px)` difumina lo que se ve detrás de él (efecto "vidrio esmerilado").
* **Transición de más de una propiedad a la vez**: `transition: transform 0.2s ease, color 0.2s ease;` anima `transform` y `color` en simultáneo, cada una con su propia duración y curva (separadas por coma, como las sombras múltiples de `box-shadow`).

> Nota: el archivo original tenía dos puntos y coma seguidos al final de la línea de `transition` (`;;`). Es un error de tipeo sin efecto real (CSS lo ignora), pero se corrigió a un solo `;` en la versión devuelta en `landing-page.css`.

---

# Ejemplo práctico: formulario animado (floating label)

```css
:root {
    --main-color: #3866f2;
}

* {
    margin: 0;
    box-sizing: border-box;
}

body {
    font-family: "JetBrains Mono", monospace;
    background-color: #e5e5f7;
    display: flex;
    align-items: center;
    min-height: 100vh;
}

.form {
    background-color: white;
    width: 90%;
    max-width: 400px;
    margin: 0 auto;
    padding: 4.5em 3em;
    border-radius: 10px;
    box-shadow: 0 5px 10px -5px rgb(0, 0, 0, 0.3);
    text-align: center;
}

.form__title {
    font-size: 2rem;
    margin-bottom: 0.5em;
}

.form__paragraph {
    font-weight: 300;
}

.form__link {
    font-weight: 400;
    color: black;
}

.form__container {
    margin-top: 3em;
    display: grid;
    gap: 2.5em;
}

.form__group {
    position: relative;
    --color: #5757577e;
}

.form__input {
    width: 100%;
    background: none;
    font-family: inherit;
    font-size: 1rem;
    color: #706c6c;
    padding: 0.6em 0.3em;
    outline: none;
    border: none;
    border-bottom: 1px solid var(--color);
}

.form__input:not(:placeholder-shown) + .form__label,
.form__input:focus + .form__label {
    transform: translateY(-12px) scale(0.7);
    transform-origin: top left;
    color: var(--main-color);
}

.form__label {
    color: var(--color);
    cursor: pointer;
    position: absolute;
    top: 0px;
    left: 5px;
    transform: translateY(10px);
    transition: transform 0.5s, color 0.3s;
}

.form__submit {
    background-color: var(--main-color);
    color: #fff;
    font-family: inherit;
    font-size: 1rem;
    padding: 0.8em 0;
    border: none;
    border-radius: 0.5em;
}

.form__line {
    position: absolute;
    bottom: 0px;
    left: 5px;
    width: 100%;
    height: 1px;
    background-color: var(--main-color);
    transform: scale(0);
    transform-origin: left bottom;
    transition: transform 0.4s;
}

.form__input:not(:placeholder-shown) ~ .form__line,
.form__input:focus ~ .form__line {
    transform: scale(1);
}
```

Este ejemplo implementa un patrón muy usado en formularios modernos: el **floating label** (etiqueta flotante), donde el texto del campo empieza superpuesto al input y "flota" hacia arriba en cuanto el usuario escribe o hace foco.

* **`:placeholder-shown`** permite detectar si el input está vacío. `:not(:placeholder-shown)` detecta lo contrario: que ya tiene contenido.
* Combinando `:not(:placeholder-shown)` y `:focus` con el selector de hermano adyacente (`.form__input + .form__label`), la etiqueta sube y se achica tanto si el campo tiene contenido como si está enfocado, aunque esté vacío.
* `.form__line` usa el selector de hermano **general** (`~`), porque no está pegado inmediatamente después del `input` en el HTML (la etiqueta `.form__label` está en el medio). Por eso no podía usarse `+` para llegar hasta `.form__line`.
* `transform-origin: top left` en `.form__label` hace que, al achicarse con `scale(0.7)`, la etiqueta se encoja desde su esquina superior izquierda (donde ya está posicionada) y no desde su centro, que la desplazaría de forma extraña.
* `--color` se declara dentro de `.form__group`, no en `:root`, por lo que su alcance queda limitado a ese grupo y sus hijos (`.form__input`, `.form__label`).

> Nota sobre un posible error a revisar: en el bloque `.form__input:not(:placeholder-shown) ~ .form__line, .form__input:focus ~ .form__line`, el código original repetía las mismas propiedades que la regla de `.form__label` (`translateY(-12px) scale(.7)`, `transform-origin: top left`, `color: var(--main-color)`) y agregaba `transform: scale(1)` al final. Por la cascada, dentro de esa misma regla solo se aplica la última declaración de `transform` (`scale(1)`), por lo que las tres primeras líneas quedaban sin efecto real; en la versión limpia de arriba se dejaron solo las propiedades que realmente hacen falta para animar la línea (`transform: scale(1)`).