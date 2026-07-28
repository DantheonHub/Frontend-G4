# Biblioteca de conceptos CSS

## Índice

* [Selector de clase](#selector-de-clase)
* [Colores](#colores)
* [Texto](#texto)
* [Modelo de caja](#modelo-de-caja)
* [Ancho y alto](#ancho-y-alto)
* [Padding](#padding)
* [Bordes](#bordes)
* [Margin](#margin)
* [`box-sizing`](#box-sizing)
* [Tipos de caja](#tipos-de-caja)
* [Centrado con `margin: auto`](#centrado-con-margin-auto)
* [Colapso de márgenes](#colapso-de-márgenes)
* [Sobrescritura de propiedades](#sobrescritura-de-propiedades)
* [Selector universal y reset](#selector-universal-y-reset)
* [Unidad `px`](#unidad-px)
* [Ejemplo completo](#ejemplo-completo)

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

```css
color: red;
color: #ff0000;
color: rgb(255, 0, 0);
color: rgba(255, 0, 0, 0.5);
color: hsl(0, 100%, 50%);
```

### Nombre

```css
color: red;
```

Es fácil de leer, aunque ofrece menos precisión.

### Hexadecimal

```css
color: #ff0000;
```

Su estructura habitual es:

```text
#RRGGBB
```

```text
RR → rojo
GG → verde
BB → azul
```

### RGB

```css
color: rgb(255, 0, 0);
```

Cada valor representa la intensidad de rojo, verde y azul.

### RGBA

```css
color: rgba(255, 0, 0, 0.5);
```

El último valor controla la transparencia:

```text
0   → transparente
0.5 → semitransparente
1   → opaco
```

### HSL

```css
color: hsl(0, 100%, 50%);
```

Representa tono, saturación y luminosidad.

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

# Unidad `px`

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

---

# Ejemplo completo

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


/* Tamaño general del texto */

body {
  font-size: 25px;
}


/* Ejemplo de box-sizing */

.element {
  width: 250px;
  height: 250px;
  background-color: teal;
  border: 30px solid blue;
  padding: 30px;
  margin: 0 auto;
}


/* Elemento de bloque */

.block {
  display: block;
  background-color: teal;
  color: white;
  margin-bottom: 30px;
}


/* Elemento en línea */

.inline {
  display: inline;
  background-color: purple;
  color: white;
}


/* Elemento en línea con propiedades de bloque */

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
