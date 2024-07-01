# Ciertos errores a evitar

## Caso 1
En casos como el siguiente:
```json
{
  "type": "paragraph",
  "text": "En inglés, se hace una distinción entre los pronombres que actúan como sujeto ({SNIPPET}) y los que funcionan como objeto ({SNIPPET}).",
  "options": [
    ["subject pronouns", "object pronouns"],
    ["object pronouns", "subject pronouns"]
  ],
  "rightOptions": [0, 1]
},
```
Evita (1) repetir lo mismo pero en inglés [`sujeto` y `subject pronouns`]; y (2) cambia el contenido de las listas para que no sea idéntico. Así el usuario no podrá seleccionar por descarte en la segunda ocasión. Por ejemplo, este componente debería ser:

```json
{
  "type": "paragraph",
  "text": "En inglés, se hace una distinción entre los pronombres que actúan como {SNIPPET} y los que funcionan como {SNIPPET}.",
  "options": [
    ["sujeto", "abstracción"],
    ["verbo", "objeto"]
  ],
  "rightOptions": [0, 1]
},
```
Intenta también que las opciones estén relacionadas si no son idénticas.

## Caso 2
Asimismo, intenta que los títulos sean minimalistas a la vez que descriptivos. Al tratarse de una academia de inglés, y estar el usuario aprendiendo en una app en un curso de inglés, no hace falta tener un `title` con el `text` "Pronombres personales en inglés". Sería mejor que fuera simplemente "Pronombres personales". Por ejemplo, en vez de:
```json
{
  "type": "title",
  "text": "Notas adicionales sobre pronombres en inglés",
  "header": false
},
```
Pon:
```json
{
  "type": "title",
  "text": "Notas adicionales sobre pronombres",
  "header": false
},
```
Es bastante evidente que se refiere a los pronombres en inglés al ser una lección de un curso de gramática de inglés.

## Caso 3
Procura añadir todo el contenido de la fuente de información. Si una lección aborda 5 conceptos y lo hace con un alto grado de detalle, trata tú también los 5 conceptos y hazlo con un alto grado de detalle.

## Caso 4
Incluye todos los componentes en grupos, y los grupos en secciones. No incluyas grupos en grupos, ni secciones en secciones. Es decir, EVITA:
```json
{
  "type": "section",
  "children": [
    {
      "type": "notification",
      "text": "Nota: «Aquella pizza» puede referirse a una pizza que acabamos de comer o a una que comimos en las vacaciones del año pasado."
    }
  ]
}
```
Y pon:

```json
{
  "type": "section",
  "children": [
    {
      "type": "group",
      "children": [
        {
          "type": "notification",
          "text": "Nota: «Aquella pizza» puede referirse a una pizza que acabamos de comer o a una que comimos en las vacaciones del año pasado."
        }
      ]
    }
  ]
}
```

## Caso 5
En las opciones, pon entre 1 y 3, usualmente dos. NUNCA hagas algo como esto:
```json
{
  "type": "paragraph",
  "text": "Los pronombres reflexivos son: {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}.",
  "options": [
    ["myself", "yourself", "himself", "herself", "itself", "ourselves", "yourselves", "themselves"],
    ["myself", "yourself", "himself", "herself", "itself", "ourselves", "yourselves", "themselves"],
    ["myself", "yourself", "himself", "herself", "itself", "ourselves", "yourselves", "themselves"],
    ["myself", "yourself", "himself", "herself", "itself", "ourselves", "yourselves", "themselves"],
    ["myself", "yourself", "himself", "herself", "itself", "ourselves", "yourselves", "themselves"],
    ["myself", "yourself", "himself", "herself", "itself", "ourselves", "yourselves", "themselves"],
    ["myself", "yourself", "himself", "herself", "itself", "ourselves", "yourselves", "themselves"],
    ["myself", "yourself", "himself", "herself", "itself", "ourselves", "yourselves", "themselves"]
  ],
  "rightOptions": [0, 1, 2, 3, 4, 5, 6, 7]
}
```
En su lugar, debería ser:
```json
{
  "type": "paragraph",
  "text": "Los pronombres reflexivos son: {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}, {SNIPPET}.",
  "options": [
    ["myself", "my"],
    ["yourself", "yours"],
    ["his", "himself"],
    ["herself", "hers"],
    ["itself", "its"],
    ["outers", "ourselves"],
    ["yourself", "yourselves"],
    ["them", "themselves"]
  ],
  "rightOptions": [0, 0, 1, 0, 0, 1, 1, 1]
}
```
Solo pon 3 por caso cuando tiene mucho sentido y cada token es pequeño:
```json
{
  "type": "example",
  "children": [
    {
      "mainText": "This is {SNIPPET} house.",
      "subText": "Ésta es mi casa.",
      "options": [
        ["my", "his", "her"]
      ],
      "rightOptions": [0]
    },
    ...
  ]
}
```

Solo pon 1 por caso cuando la respuesta es tan poco intuitiva o inimaginable para el usuario que no tenga ni idea de qué responder:
```json
{
  "type": "paragraph",
  "text": "Es importante comenzar señalando que los pronombres demostrativos pueden estar en singular o {SNIPPET} y que pueden hacer referencia a la {SNIPPET}.",
  "options": [
    ["estoico", "plural"],
    ["distancia"]
  ],
  "rightOptions": [1, 0]
}
```
