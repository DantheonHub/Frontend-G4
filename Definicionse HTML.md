# Biblioteca de conceptos HTML

Esta biblioteca reúne los conceptos fundamentales de HTML vistos durante el Bootcamp Frontend G4 de Código Facilito.

---

## Índice

- [Biblioteca de conceptos HTML](#biblioteca-de-conceptos-html)
  - [Índice](#índice)
- [¿Qué es HTML?](#qué-es-html)
- [Historia breve de HTML](#historia-breve-de-html)
- [Estructura básica de un documento HTML](#estructura-básica-de-un-documento-html)
- [`DOCTYPE`](#doctype)
- [Etiqueta `html`](#etiqueta-html)
- [Atributo `lang`](#atributo-lang)
- [Etiqueta `head`](#etiqueta-head)
- [Etiqueta `meta`](#etiqueta-meta)
- [Codificación con `charset`](#codificación-con-charset)
- [`meta viewport`](#meta-viewport)
  - [`name="viewport"`](#nameviewport)
  - [`width=device-width`](#widthdevice-width)
  - [`initial-scale=1.0`](#initial-scale10)
- [Etiqueta `title`](#etiqueta-title)
- [Etiqueta `link`](#etiqueta-link)
- [Atributos `rel` y `href`](#atributos-rel-y-href)
  - [`rel`](#rel)
  - [`href`](#href)
- [Etiqueta `body`](#etiqueta-body)
- [Encabezados](#encabezados)
- [Párrafos](#párrafos)
- [Saltos de línea](#saltos-de-línea)
- [Contenedores con `div`](#contenedores-con-div)
- [Enlaces](#enlaces)
- [Rutas relativas](#rutas-relativas)
  - [Archivo en la misma carpeta](#archivo-en-la-misma-carpeta)
  - [Archivo dentro de otra carpeta](#archivo-dentro-de-otra-carpeta)
- [Rutas absolutas](#rutas-absolutas)
- [Abrir enlaces en otra pestaña](#abrir-enlaces-en-otra-pestaña)
- [Imágenes](#imágenes)
  - [Atributo `src`](#atributo-src)
  - [Atributo `alt`](#atributo-alt)
- [Listas ordenadas](#listas-ordenadas)
- [Listas desordenadas](#listas-desordenadas)
- [Navegación semántica](#navegación-semántica)
- [Archivo `index.html`](#archivo-indexhtml)
- [Etiquetas y atributos](#etiquetas-y-atributos)
  - [Etiquetas registradas](#etiquetas-registradas)
  - [Atributos registrados](#atributos-registrados)
- [Ejemplo completo](#ejemplo-completo)
  - [Estructura del ejemplo](#estructura-del-ejemplo)

---

# ¿Qué es HTML?

HTML significa **HyperText Markup Language**, o lenguaje de marcado de hipertexto.

Se utiliza para definir la estructura y el contenido de una página web.

HTML permite representar elementos como:

* títulos;
* párrafos;
* enlaces;
* imágenes;
* listas;
* secciones;
* formularios.

HTML no es un lenguaje de programación. Es un lenguaje de marcado porque utiliza etiquetas para describir la función de cada contenido.

```html
<h1>Título principal</h1>

<p>Este es un párrafo.</p>
```

En este ejemplo:

* `<h1>` representa un encabezado principal;
* `<p>` representa un párrafo.

HTML define la estructura, CSS controla la apariencia y JavaScript agrega comportamiento.

---

# Historia breve de HTML

HTML fue creado por Tim Berners-Lee a comienzos de la década de 1990.

Su objetivo inicial era permitir que documentos científicos pudieran conectarse mediante enlaces.

El nombre HTML se compone de:

```text
HyperText
→ texto conectado con otros documentos mediante enlaces.

Markup Language
→ lenguaje que utiliza etiquetas para describir contenido.
```

Con el crecimiento de la web, los navegadores comenzaron a incorporar funciones propias. Esto provocó diferencias entre ellos y dificultó que una misma página funcionara igual en todos.

Para resolver ese problema se desarrollaron estándares comunes.

Actualmente, HTML se mantiene como un estándar web en evolución.

La expresión **HTML5** se utiliza para identificar la versión moderna de HTML.

---

# Estructura básica de un documento HTML

Una página HTML utiliza una estructura base:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8">

    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    >

    <title>Título de la página</title>
  </head>

  <body>
    <h1>Contenido principal</h1>
  </body>
</html>
```

La estructura principal es:

```text
html
├── head
└── body
```

* `head` contiene información y configuración del documento.
* `body` contiene el contenido visible de la página.

---

# `DOCTYPE`

La declaración:

```html
<!DOCTYPE html>
```

indica que el documento utiliza HTML moderno.

Debe aparecer al principio del archivo:

```html
<!DOCTYPE html>
<html lang="es">
</html>
```

`DOCTYPE` no es una etiqueta HTML convencional. Es una declaración que ayuda al navegador a interpretar correctamente el documento.

---

# Etiqueta `html`

La etiqueta `<html>` contiene todo el documento.

```html
<html lang="es">
  <head></head>
  <body></body>
</html>
```

Es el elemento raíz de la página.

Dentro de ella se encuentran normalmente:

```html
<head></head>
<body></body>
```

---

# Atributo `lang`

El atributo `lang` indica el idioma principal del documento.

```html
<html lang="es">
```

En este ejemplo:

```text
lang → atributo
es   → valor
```

`es` representa el idioma español.

Otros ejemplos:

```html
<html lang="en">
<html lang="pt">
<html lang="fr">
```

Indicar el idioma ayuda a:

* lectores de pantalla;
* motores de búsqueda;
* traductores automáticos;
* navegadores.

---

# Etiqueta `head`

La etiqueta `<head>` contiene información y configuración del documento.

```html
<head>
  <meta charset="UTF-8">
  <title>Mi página</title>
</head>
```

Su contenido normalmente no aparece de forma visible en la página.

Puede contener etiquetas como:

```html
<meta>
<title>
<link>
```

```text
head
├── meta
├── title
└── link
```

---

# Etiqueta `meta`

La etiqueta `<meta>` agrega metadatos sobre el documento.

Los metadatos son información que describe o configura la página.

```html
<meta charset="UTF-8">
```

También puede utilizar atributos como `name` y `content`:

```html
<meta
  name="description"
  content="Descripción de la página"
>
```

En este ejemplo:

```text
name
→ indica el tipo de metadato.

content
→ contiene su valor.
```

La etiqueta `<meta>` no necesita una etiqueta de cierre.

---

# Codificación con `charset`

El atributo `charset` define la codificación de caracteres.

```html
<meta charset="UTF-8">
```

`UTF-8` permite mostrar correctamente:

* letras con tilde;
* la letra `ñ`;
* símbolos;
* caracteres de distintos idiomas.

La forma habitual es:

```html
<head>
  <meta charset="UTF-8">
</head>
```

Sin una codificación adecuada, algunos caracteres pueden mostrarse incorrectamente.

---

# `meta viewport`

La etiqueta:

```html
<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0"
>
```

configura cómo se muestra la página en distintos dispositivos.

## `name="viewport"`

Indica que el metadato configura el área visible de la página.

## `width=device-width`

Hace que el ancho de la página coincida con el ancho de la pantalla del dispositivo.

## `initial-scale=1.0`

Establece el nivel de zoom inicial.

La forma habitual es:

```html
<head>
  <meta
    name="viewport"
    content="width=device-width, initial-scale=1.0"
  >
</head>
```

---

# Etiqueta `title`

La etiqueta `<title>` define el título del documento.

```html
<title>Mi primera página</title>
```

Este texto aparece normalmente en:

* la pestaña del navegador;
* los marcadores;
* los resultados de búsqueda.

Debe colocarse dentro de `head`:

```html
<head>
  <title>Mi primera página</title>
</head>
```

No representa un título visible dentro de la página.

Para el título visible se utiliza un encabezado:

```html
<title>Título de la pestaña</title>

<h1>Título visible de la página</h1>
```

---

# Etiqueta `link`

La etiqueta `<link>` conecta el documento con un recurso externo.

Su uso frecuente es enlazar una hoja de estilos CSS:

```html
<link rel="stylesheet" href="styles.css">
```

Se coloca dentro de `head`:

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

La etiqueta `<link>` no necesita una etiqueta de cierre.

---

# Atributos `rel` y `href`

## `rel`

El atributo `rel` indica la relación entre el documento y el recurso enlazado.

```html
rel="stylesheet"
```

El valor `stylesheet` indica que el recurso es una hoja de estilos.

## `href`

El atributo `href` indica la ubicación del recurso.

```html
href="styles.css"
```

Ejemplo completo:

```html
<link rel="stylesheet" href="styles.css">
```

```text
link
├── rel="stylesheet" → tipo de relación
└── href="styles.css" → ubicación del archivo
```

`href` también se utiliza en los enlaces creados con `<a>`.

---

# Etiqueta `body`

La etiqueta `<body>` contiene el contenido visible de la página.

```html
<body>
  <h1>Título principal</h1>
  <p>Contenido de la página.</p>
</body>
```

Dentro de `body` pueden incluirse:

* encabezados;
* párrafos;
* enlaces;
* imágenes;
* listas;
* contenedores;
* secciones.

Solo debe existir un elemento `<body>` dentro del documento.

---

# Encabezados

HTML dispone de seis niveles de encabezados:

```html
<h1>Encabezado principal</h1>
<h2>Encabezado de segundo nivel</h2>
<h3>Encabezado de tercer nivel</h3>
<h4>Encabezado de cuarto nivel</h4>
<h5>Encabezado de quinto nivel</h5>
<h6>Encabezado de sexto nivel</h6>
```

Los encabezados representan la jerarquía del contenido.

```text
h1
├── h2
│   ├── h3
│   └── h3
└── h2
```

Ejemplo:

```html
<h1>HTML</h1>

<h2>Etiquetas básicas</h2>

<h3>Párrafos</h3>
<h3>Enlaces</h3>

<h2>Formularios</h2>
```

`h1` representa el encabezado principal.

Los números no deben elegirse solamente por el tamaño visual. Su función principal es indicar jerarquía.

---

# Párrafos

La etiqueta `<p>` representa un párrafo.

```html
<p>HTML permite estructurar una página web.</p>
```

Cada párrafo forma un bloque independiente:

```html
<p>Primer párrafo.</p>

<p>Segundo párrafo.</p>
```

El navegador ignora normalmente los espacios adicionales y los saltos de línea escritos dentro del código:

```html
<p>
  Este texto
  está escrito
  en varias líneas.
</p>
```

Se mostrará como un párrafo continuo.

---

# Saltos de línea

La etiqueta `<br>` genera un salto de línea.

```html
<p>
  Primera línea.<br>
  Segunda línea.
</p>
```

Resultado:

```text
Primera línea.
Segunda línea.
```

`br` no necesita una etiqueta de cierre.

Se utiliza cuando el salto forma parte del contenido, como en:

* direcciones;
* poemas;
* letras;
* textos con líneas específicas.

Para separar párrafos deben utilizarse varias etiquetas `<p>`:

```html
<p>Primer párrafo.</p>
<p>Segundo párrafo.</p>
```

No es conveniente utilizar varios `<br>` para crear espacio visual. Ese espacio se controla con CSS.

---

# Contenedores con `div`

La etiqueta `<div>` es un contenedor genérico.

Permite agrupar varios elementos:

```html
<div>
  <h2>Curso de HTML</h2>
  <p>Contenido del curso.</p>
  <a href="curso.html">Ver curso</a>
</div>
```

`div` no describe por sí misma el significado del contenido.

Se utiliza para:

* organizar elementos;
* aplicar estilos;
* agrupar contenido;
* tratar varios elementos como una unidad.

Ejemplo con una clase:

```html
<div class="tarjeta">
  <h2>HTML</h2>
  <p>Lenguaje de marcado.</p>
</div>
```

```css
.tarjeta {
  background-color: lightgray;
}
```

Cuando existe una etiqueta semántica que describe mejor el contenido, suele ser más conveniente utilizarla.

---

# Enlaces

La etiqueta `<a>` permite crear enlaces.

La letra `a` proviene de **anchor**, que significa ancla.

```html
<a href="ejemplo.html">Ir a Ejemplo</a>
```

Su estructura es:

```text
<a href="destino">Texto visible</a>
```

* `<a>` crea el enlace;
* `href` define el destino;
* el contenido es el texto visible.

`href` significa **Hypertext Reference**, o referencia de hipertexto.

```html
<a href="contacto.html">Ir a contacto</a>
```

Sin `href`, la etiqueta no funciona como un enlace convencional.

---

# Rutas relativas

Una ruta relativa indica la ubicación de un archivo tomando como referencia el documento actual.

Se utiliza para archivos internos del proyecto.

## Archivo en la misma carpeta

```html
<a href="ejemplo.html">Ir a Ejemplo</a>
```

Estructura:

```text
proyecto
├── index.html
└── ejemplo.html
```

Desde `index.html` se puede acceder escribiendo:

```text
ejemplo.html
```

## Archivo dentro de otra carpeta

```html
<a href="paginas/ejemplo.html">Ir a Ejemplo</a>
```

Estructura:

```text
proyecto
├── index.html
└── paginas
    └── ejemplo.html
```

La ruta sigue esta forma:

```text
carpeta/archivo.extensión
```

Ejemplo con una imagen:

```html
<img
  src="img/Personajebase.png"
  alt="Personaje base"
>
```

Estructura:

```text
proyecto
├── index.html
└── img
    └── Personajebase.png
```

---

# Rutas absolutas

Una ruta absoluta contiene la dirección completa de un recurso externo.

```html
<a href="https://www.google.com">Ir a Google</a>
```

Las direcciones externas deben incluir el protocolo:

```text
https://
```

Forma correcta:

```html
<a href="https://www.google.com">
  Ir a Google
</a>
```

Forma incompleta:

```html
<a href="www.google.com">
  Ir a Google
</a>
```

---

# Abrir enlaces en otra pestaña

El atributo:

```html
target="_blank"
```

abre el enlace en una nueva pestaña o ventana.

```html
<a
  href="https://www.google.com"
  target="_blank"
>
  Ir a Google
</a>
```

La forma recomendada para enlaces externos es:

```html
<a
  href="https://www.google.com"
  target="_blank"
  rel="noopener noreferrer"
>
  Ir a Google
</a>
```

`rel="noopener noreferrer"` evita que la página externa tenga acceso innecesario a la página de origen.

---

# Imágenes

La etiqueta `<img>` muestra una imagen.

```html
<img
  src="img/Personajebase.png"
  alt="Personaje base"
>
```

No necesita una etiqueta de cierre.

Sus atributos principales son:

```text
src → ubicación de la imagen
alt → descripción alternativa
```

## Atributo `src`

`src` significa **source**, o fuente.

Indica la ruta del archivo:

```html
<img
  src="img/Personajebase.png"
  alt="Personaje base"
>
```

La ruta:

```text
img/Personajebase.png
```

significa:

1. entrar en la carpeta `img`;
2. buscar el archivo `Personajebase.png`.

## Atributo `alt`

`alt` define el texto alternativo de una imagen.

```html
<img
  src="img/Personajebase.png"
  alt="Personaje base"
>
```

El texto alternativo es útil cuando:

* la imagen no puede cargarse;
* una persona utiliza un lector de pantalla;
* un buscador interpreta el contenido.

Ejemplo más descriptivo:

```html
<img
  src="img/Personajebase.png"
  alt="Personaje 3D de cuerpo completo sin armadura"
>
```

No es necesario comenzar con expresiones como “imagen de”, porque el lector de pantalla ya identifica el elemento como una imagen.

Si la imagen es decorativa:

```html
<img src="img/decoracion.png" alt="">
```

---

# Listas ordenadas

La etiqueta `<ol>` significa **ordered list** y crea una lista ordenada.

Cada elemento se representa con `<li>`, que significa **list item**.

```html
<ol>
  <li>Primer paso</li>
  <li>Segundo paso</li>
  <li>Tercer paso</li>
</ol>
```

Resultado:

```text
1. Primer paso
2. Segundo paso
3. Tercer paso
```

Se utiliza cuando el orden es importante:

* instrucciones;
* procedimientos;
* clasificaciones;
* secuencias.

La estructura es:

```text
ol
├── li
├── li
└── li
```

---

# Listas desordenadas

La etiqueta `<ul>` significa **unordered list** y crea una lista sin orden numérico.

```html
<ul>
  <li>HTML</li>
  <li>CSS</li>
  <li>JavaScript</li>
</ul>
```

Resultado:

```text
• HTML
• CSS
• JavaScript
```

Se utiliza cuando el orden de los elementos no es importante.

La estructura es:

```text
ul
├── li
├── li
└── li
```

Tanto `<ol>` como `<ul>` utilizan elementos `<li>`.

---

# Navegación semántica

La etiqueta `<nav>` representa una sección de navegación.

```html
<nav>
  <ul>
    <li>
      <a href="index.html">Ir al inicio</a>
    </li>

    <li>
      <a href="ejemplo.html">Nosotros</a>
    </li>
  </ul>
</nav>
```

La estructura es:

```text
nav
└── ul
    ├── li
    │   └── a
    └── li
        └── a
```

Cada etiqueta cumple una función:

| Etiqueta | Función                              |
| -------- | ------------------------------------ |
| `nav`    | Identifica una sección de navegación |
| `ul`     | Agrupa los enlaces                   |
| `li`     | Representa cada opción               |
| `a`      | Crea el enlace                       |
| `href`   | Indica el destino                    |

`nav` aporta significado a la estructura del documento.

No modifica por sí sola la apariencia de los enlaces.

No todos los grupos de enlaces necesitan estar dentro de `nav`. Se utiliza principalmente para bloques importantes de navegación.

---

# Archivo `index.html`

El archivo `index.html` suele utilizarse como página principal de un sitio o una carpeta.

```text
proyecto
├── index.html
└── ejemplo.html
```

Al ingresar a la dirección principal del sitio, el servidor suele buscar un archivo llamado `index.html`.

Por ejemplo:

```text
https://misitio.com/
```

puede cargar automáticamente:

```text
https://misitio.com/index.html
```

Por eso, un enlace hacia la página principal puede escribirse así:

```html
<a href="index.html">Ir al inicio</a>
```

También puede utilizarse:

```html
<a href="/">Ir al inicio</a>
```

`index.html` es una convención habitual. No es una etiqueta ni una regla propia de HTML.

---

# Etiquetas y atributos

## Etiquetas registradas

| Etiqueta    | Función                              |
| ----------- | ------------------------------------ |
| `html`      | Contiene todo el documento           |
| `head`      | Contiene información y configuración |
| `body`      | Contiene el contenido visible        |
| `title`     | Define el título de la pestaña       |
| `meta`      | Agrega metadatos                     |
| `link`      | Enlaza recursos externos             |
| `h1` a `h6` | Representan encabezados              |
| `p`         | Representa un párrafo                |
| `br`        | Genera un salto de línea             |
| `div`       | Agrupa contenido                     |
| `a`         | Crea un enlace                       |
| `img`       | Muestra una imagen                   |
| `ol`        | Crea una lista ordenada              |
| `ul`        | Crea una lista desordenada           |
| `li`        | Representa un elemento de lista      |
| `nav`       | Representa una sección de navegación |

## Atributos registrados

| Atributo  | Función                           |
| --------- | --------------------------------- |
| `lang`    | Indica el idioma del documento    |
| `charset` | Define la codificación            |
| `name`    | Identifica el tipo de metadato    |
| `content` | Contiene el valor de un metadato  |
| `rel`     | Define la relación con un recurso |
| `href`    | Indica el destino de un enlace    |
| `src`     | Indica la ubicación de una imagen |
| `alt`     | Describe una imagen               |
| `target`  | Define dónde se abre un enlace    |
| `class`   | Asigna una clase                  |
| `id`      | Identifica un elemento            |

---

# Ejemplo completo

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8">

    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    >

    <title>Biblioteca de HTML</title>

    <link rel="stylesheet" href="styles.css">
  </head>

  <body>
    <nav>
      <ul>
        <li>
          <a href="index.html">Inicio</a>
        </li>

        <li>
          <a href="ejemplo.html">Nosotros</a>
        </li>

        <li>
          <a
            href="https://www.google.com"
            target="_blank"
            rel="noopener noreferrer"
          >
            Google
          </a>
        </li>
      </ul>
    </nav>

    <div>
      <h1>Fundamentos de HTML</h1>

      <p>
        HTML es un lenguaje de marcado utilizado para estructurar
        el contenido de una página web.
      </p>

      <img
        src="img/Personajebase.png"
        alt="Personaje base"
      >
    </div>

    <div>
      <h2>Temas aprendidos</h2>

      <ol>
        <li>Estructura básica.</li>
        <li>Encabezados y párrafos.</li>
        <li>Enlaces e imágenes.</li>
        <li>Listas y navegación.</li>
      </ol>

      <h2>Tecnologías</h2>

      <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
      </ul>
    </div>
  </body>
</html>
```

## Estructura del ejemplo

```text
html
├── head
│   ├── meta charset
│   ├── meta viewport
│   ├── title
│   └── link
└── body
    ├── nav
    │   └── ul
    │       └── li
    │           └── a
    ├── div
    │   ├── h1
    │   ├── p
    │   └── img
    └── div
        ├── h2
        ├── ol
        │   └── li
        ├── h2
        └── ul
            └── li
```
