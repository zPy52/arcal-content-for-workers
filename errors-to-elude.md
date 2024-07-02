# Ciertos errores a evitar

## Caso 0 (reglas generales de estilización)
El lenguaje ha de ser formal, tratando de usted al usuario cuando se refiera a él. Por ejemplo, en vez de decir «tienes que tener cuidado con la forma del plural», se ha de decir «tenga cuidado con la forma del plural». Asimismo, ha de usarse un tono y vocabulario propio del español de España, diciendo «aquí» en lugar de «acá», o «vídeo» en vez de «video». 

Hay una excepción a esta regla y es cuando solo hablar con el español de España sonara redundante. Por ejemplo, si se ha dicho muchas veces la palabra «aquí» se puede decir «acá» para variar y enriquecer el mensaje. Esta excepción no aplica a los acentos (no vale expresar «¿qué hacés?» en vez de «¿qué haces?»).

De la misma manera, al entrecomillar o referirse a un texto inglés, se ha de poner en *cursiva*, pudiendo añadirse **negrita** u otros efectos semejantes si se desea y es adecuado para el caso. Por ejemplo, al decir «la expresión *hold your ground* significa "mantenerse firme"» o en «la forma plural del pronombre es igual que para el singular (*you*)».

Por supuesto, ha de cuidarse que la gramática y ortografía de todos los mensajes sean correctos, y no haya indiscreciones como colocar un signo de puntuación al lado de una letra,como en este caso.O en este otro. 

Asimismo, es menester ajustar un mensaje al formato de una aplicación móvil. En caso de tener un fragmento de texto gigantesco, tal vez sea buena idea resumirlo o partirlo en varios párrafos para que no quede como un bloque monolítico gigante en la pantalla. Puede utilizar el [visualizador de payloads JSON](https://arcal-gt-visualizer.tiiny.site) para ayudarle. 

De la misma forma, intente en la medida de lo posible explicar el contenido que encuentre en la web con sus propias palaras, a fin de que no sea una copia exacta de la web. Cree sus propios ejemplos en la medida de lo posible, basándose en los que se encuentran en la web. Por ejemplo, en vez de copiar «*bath (towel)*» (en la [lección de adjetivos del nivel básico](https://www.curso-ingles.com/aprender/cursos/nivel-basico/adjectives/adjectives)), se puede poner «*kitchen (table)*, *garden (tool)*...».

Una buena brújula o estrella polar para cómo expresar algo con sus palabras es preguntarse *¿cómo puedo hacer inevitable que el estudiante entienda a la perfección el concepto?* y *¿qué dudas podría tener o podría generarle este contenido, y cómo podría mejorarlas?*. Esto le llevará también a profundizar en el mensaje y enriquecerlo, mejorando con muchísimas creces la experiencia y aprendizaje del usuario. Por ejemplo, en:

> **Nota: En inglés no existe la forma “usted” o “ustedes” formal.** Por lo tanto los nativos de la lengua ni siquiera lo tienen conceptualizado como una forma aquí llamada “formal”. Se tiene que entender por tanto, que la forma masculina, femenina y neutra son lo mismo, lo único que las diferencia es el género.
>
> Además, ten en cuenta que **en inglés sólo existe una forma para “tú” y “vosotros”, “you”**, excepto en la forma reflexiva que distingue entre el singular (yourself) y plural (yourselves).

Podría transformarse en:

> **Nota: En inglés no existe la forma “usted” o “ustedes” formal.** Por lo tanto los nativos de la lengua ni siquiera lo tienen conceptualizado como algo “formal” o que pueda tenera una versión formal. Esto aplica tanto para el masculino, femenino, neutro y plural: no hay pronombres exclusivamente formales.
>
> Para referir formalidad, ha de usarse otras expresiones como «*sir*» (caballero, señor) o «*His Majesty*» (Su Majestad).
>
> Además, tenga en cuenta que **en inglés sólo existe una forma para «tú» y «vosotros»: «<i>you</i>»**, excepto en la forma reflexiva que distingue entre el singular (<i>yourself</i>) y plural (<i>yourselves</i>).


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
En las opciones, pon entre 1 y 3, usualmente dos. **NUNCA** hagas algo como esto:
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

## Caso 6 
Siempre que se pueda, ha de usarse las comillas españolas «» en lugar de las inglesas "" o simples ''. Estas últimas solo se usan dentro de las españolas, para entrecomillar un fragmento ya entrecomillado. Por ejemplo:

> Yo ya se lo había advertido: «Ten cuidado, que se rompe». Al poco rato, se me acerca con una rueda en la mano y carita compungida: «Se me ha "rompido" sin querer». Y le digo, conteniendo la risa: «¿Cómo que "se me ha 'rompido' sin querer"?».


## Caso 7
Las notificaciones han de ser muy pequeñas en contenido. Estas aparecen en la app como una notificación de WhatsApp lo hace en un iPhone: cayendo desde arriba y ocupando parte de la pantalla. Por su naturaleza intrusiva, estos componentes han de ser especialmente pequeños. Cuando se tenga una nota muy grande, los detalles han de explicarse en un párrafo. Las notificaciones solo están para apuntes muy rápidos, fugaces, pequeños.

Por ejemplo, en vez de:
```json
{
  "type": "notification",
  "text": "<b>Nota: En inglés no existe la forma «usted» o «ustedes» formal.</b> Por lo tanto los nativos de la lengua ni siquiera lo tienen conceptualizado como una forma aquí llamada “formal”. Se tiene que entender por tanto, que la forma masculina, femenina y neutra son lo mismo, lo único que las diferencia es el género. Además, ten en cuenta que <B> en inglés sólo existe una forma para “tú” y “vosotros”, “you”</b>,excepto en la forma reflexiva que distingue entre el singular (<b>yourself</b>) y plural (<b>yourselves</b>)."
}
```
Puede hacer:
```json
{
  "type": "notification",
  "text": "Nota: En inglés no existe la forma «usted» o «ustedes» formal."
},
...
{
  "type": "title",
  "text": "Cómo decir «usted» en vez de «tú»"
},
{
  "type": "paragraph",
  "text": "Los nativos de la lengua ni siquiera lo tienen conceptualizado como una forma «formal». Se tiene que entender por tanto, que la forma masculina, femenina y neutra son lo mismo, lo único que las diferencia es el género."
},
{
  "type": "paragraph",
  "text": "Además, tenga en cuenta que <b>en inglés sólo existe una forma para «tú» y «vosotros»: «<i>you</i>»</b>, excepto en la forma reflexiva que distingue entre el singular (<i>yourself</i>) y plural (<i>yourselves</i>)."
}
```
