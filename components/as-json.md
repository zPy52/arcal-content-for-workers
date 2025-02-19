# Documentación de Componentes
A continuación, se detalla el listado de componentes que se pueden utilizar para representar una lección.

## 0. Section

**Descripción:** Este componente se utiliza para representar una pantalla completa (sección) en la aplicación. Contiene uno o más grupos de componentes que se mostrarán juntos. Este componente se usa para estructurar el contenido de una lección de forma lógica y manejable, permitiendo dividir el contenido en múltiples pantallas si es necesario.

**Campos:**
- `type`: Este campo debe ser siempre "section".
- `children`: Una lista de grupos que pertenecen a la pantalla/sección.

**Ejemplo:**
```json
{
  "type": "section",
  "children": [
    {
      "type": "group",
      "children": [
        {
          "type": "title",
          "header": true,
          "text": "El futuro con <b>will</b>"
        }
        {
          "type": "paragraph",
          "text": "El futuro con <b>will</b> se utiliza cuando {SNIPPET} que va a pasar algo:",
          "options": [
            ["no se está seguro de", "se sabe o se cree"]
          ],
          "rightOptions": [1]
        }
      ]
    },
    {
      "type": "group",
      "children": [
        {
          "type": "example",
          "mainText": "It will be autumn soon.",
          "subText": "Queda poco para el otoño (lit. pronto será otoño).",
          "options": []
        },
        {
          "type": "example",
          "mainText": "You'll love this book!",
          "subText": "¡Te va a encantar este libro!",
          "options": []
        }
      ]
    }
  ]
}
```
**Explicación:** Este componente contiene dos grupos. El primer grupo incluye dos componentes text, mientras que el segundo grupo incluye dos componentes example. Esta estructura permite que toda la información se muestre en una sola pantalla.

## 1. Group

**Descripción:** El componente group se utiliza para agrupar varios componentes y presentarlos juntos en la pantalla. Una vez completados los ejercicios dentro del grupo, se pueden mostrar los siguientes grupos o componentes.

**Campos:**
- `type`: Este campo debe ser siempre "group".
- `children`: Una lista de componentes que pertenecen al grupo.

**Ejemplo:**
```json
{
  "type": "group",
  "children": [
    {
      "type": "title",
      "header": true,
      "text": "El futuro con <b>will</b>"
    },
    {
      "type": "paragraph",
      "text": "El futuro con <b>will</b> se utiliza cuando {SNIPPET} que va a pasar algo:",
      "options": [
        ["no se está seguro de", "se sabe o se cree"]
      ],
      "rightOptions": [1]
    }
  ]
}
```
**Explicación:** Este grupo contiene dos componentes de texto. El primero muestra el título de la sección, mientras que el párrafo incluye un `{SNIPPET}` que el usuario debe completar seleccionando una opción.

## 2. Title

**Descripción:** El componente title se utiliza para mostrar headers o subheaders que separan el contenido dentro de una sección o grupo.

**Campos:**
- `type`: Este campo debe ser siempre "title".
- `text`: El texto a mostrar, en el que se puedan añadir etiquetas html para negritas (`<b>`), cursivas (`<i>`) o subrayado (`<u>`).
- `header`: (Opcional). Puede ser `false`, `true` o no incluirse. Si es `true`, se muestra como un título grande (piénsese en `<h1>`), mientras que con `false` o no incluyendo el campo `header` en el payload, sería un subtítulo (piénsese en `<h2>` y/o `<h3>`). Por cada screen SOLO PUEDE HABER 1 TÍTULO HEADER (`header` como `true`), aunque por cada grupo pueden haber ninguno, uno o varios títulos subheader (`header` es `false`).

**Ejemplo:**
```json
{
  "type": "title",
  "text": "El futuro con <b>will</b>",
  "header": true,
}
...
{
  "type": "title",
  "text": "Cuándo usar <i>a</i> o <i>an</i>",
}
```
**Explicación:** Este componente title se habrá de ubicar a la cabeza del primer grupo de la screen correspondiente. En el segundo caso, sobre a y an, este podría ubicarse en el lugar más adecuado dentro de un grupo que tratara esa temática.

## 3. Paragraph

**Descripción:** El componente paragraph se utiliza para mostrar párrafos de texto que pueden contener snippets `{SNIPPET}` a completar con opciones. En caso de querer confeccionar una tabla, se habrá de usar un párrafo distinto por cada fila de la misma y adaptar el contenido a una vista de párrafo en lugar de tabla (excluyendo los headers, eliminando algún que otro campo si es necesario, etc.).

**Campos:**
- `type`: Este campo debe ser siempre "paragraph".
- `text`: El texto a mostrar, que puede incluir snippets `{SNIPPET}` que deben ser completados.
- `options`: Una lista de listas de opciones para cada snippet en el texto.
- `rightOptions`: Una lista de índices que indican la opción correcta para cada snippet en la lista de options.

**Ejemplo:**
```json
{
  "type": "paragraph",
  "text": "El futuro con <b>will</b> se utiliza cuando {SNIPPET} que va a pasar algo:",
  "options": [
    ["no se está seguro de", "se sabe o se cree"]
  ],
  "rightOptions": [1]
}
```
**Explicación:** Este componente text incluye un snippet `{SNIPPET}` que el usuario debe completar seleccionando entre las opciones "no se está seguro de" y "se sabe o se cree". La opción correcta es la segunda, indicada por rightOptions: [1].

**Ejemplo 2:**
```json
{
  "type": "paragraph",
  "text": "En inglés, se hace una distinción entre los pronombres que actúan como {SNIPPET} y los que funcionan como {SNIPPET}.",
  "options": [
    ["sujeto", "abstracción"],
    ["verbo", "objecto"]
  ],
  "rightOptions": [0, 1]
}
```
**Explicación:** Este componente text incluye dos snippets `{SNIPPET}` que el usuario debe completar seleccionando entre las opciones "sujeto" y "objeto". Para ello, se proporcionan dos listas (`["sujeto", "abstracción"]` y `["verbo", "objecto"]`) junto con los índices correctos en `rightOptions` (`0` para el primer caso y `1` para el segundo).


## 4. Example

**Descripción:** El componente example se utiliza para mostrar ejemplos de oraciones en el idioma de aprendizaje con su correspondiente traducción. Estos ejemplos pueden contener snippets `{SNIPPET}` que deben ser completados con opciones.

**Campos:**
- `type`: Este campo debe ser siempre "example".
- `children`: Listado de ejemplos. Estos aparecerán uno detrás de otro, dentro de un componente Container.
- `mainText`: El texto en el idioma que se está aprendiendo (inglés en este caso), que puede incluir snippets `{SNIPPET}`.
- `subText`: La traducción del texto en el idioma nativo del usuario (español en este caso).
- `options`: (Opcional [1]) Una lista de listas de opciones para cada snippet en el texto.
- `rightOptions`: (Opcional [1]) Una lista de índices que indican la opción correcta para cada snippet en la lista de options. Si se incluye el campo `options`, se debe incluir este sí o sí.
- `validOptions`: (Opcional [2]) Una lista de listas que contiene los posibles textos que el usuario puede ingresar para completar el snippet.

El grupo de opcionales marcado con [1] no es compatible con los opcionales del [2]. Es decir, que si hay `options` y `rightOptions`, no puede haber `validOptions` y viceversa.

**Ejemplo 1 (con opciones):**
```json
{
  "type": "example",
  "children": [
    {
      "mainText": "There {SNIPPET} more women in high paying jobs.",
      "subText": "Habrá más mujeres en puestos de alta remuneración.",
      "options": [
        ["will be", "are going to be"]
      ],
      "rightOptions": [0]
    },
    {
      "mainText": "It {SNIPPET} be autumn soon.",
      "subText": "Pronto será otoño.",
      "validOptions": ["will", "'ll"],
    },
    {
      "mainText": "I'm {SNIPPET} the cinema tomorrow.",
      "subText": "Mañana iré al cine.",
      "validOptions": ["going to"],
    },
  ],
}
```
**Explicación:** Este ejemplo muestra una oración en inglés con un snippet `{SNIPPET}`. Las opciones para completar el snippet son "will be" y "are going to be", siendo la opción correcta "will be" indicada por rightOptions: [0].

**Ejemplo 2 (con validInputs):**
```json
{
  "type": "paragraph",
  "text": "I {SNIPPET} a drink after work.",
  "validInputs": [
    ["will have", "will go for"]
  ],
  "subText": "Después del trabajo voy a ir a tomar algo."
}
```
**Explicación:** En este caso, el usuario debe introducir texto para completar el snippet `{SNIPPET}`. Las respuestas válidas son "will have" y "will go for", indicadas por validInputs: [["will have", "will go for"]].

## 5. Notification

**Descripción:** El componente notification se utiliza para mostrar mensajes informativos al usuario.

**Campos:**
- `type`: Este campo debe ser siempre "notification".
- `text`: El texto del mensaje informativo a mostrar.

**Ejemplo:**
```json
{
  "type": "notification",
  "text": "La palabra <b>will</b> también puede abreviarse como 'll."
}
```
**Explicación:** Este componente muestra un mensaje informativo sobre la abreviación de "will" a "'ll". No contiene snippets ni opciones, solo texto.
