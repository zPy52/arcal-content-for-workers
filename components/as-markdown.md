# Nota:
Esta es una versión simplificada de [Documentación de Componentes (JSON)](https://github.com/zPy52/arcal-content-for-workers/blob/main/components/as-json.md). Para leer este archivo, antes ha de haberse consultado su versión JSON para comprender en profundidad a qué nos referimos con, por ejemplo, `array de números enteros json`.

Se adjunta un ejemplo al final de este archivo de una lección gramatical en JSON y en su equivalente MD.

# Nota 2:
En el texto de los componentes `Title`, `Paragraph`, `Notification` y `Example` (`Main Text` y `Sub Text`) podrá usarse la siguiente notación markdown para aplicar estilos de cursiva, negrita, etc:

- **Negrita:** Emplace el texto entre dobles asteriscos. Por ejemplo, `Esto es un **ejemplo**.` en markdown se convierte en: Esto es un **ejemplo**.
- *Cursiva:* Emplace el texto entre asteriscos. Por ejemplo, `Esto es un *ejemplo*.` en markdown se convierte en: Esto es un *ejemplo*.
- __Subrayado:__ Emplace el texto entre dobles barras bajas. Por ejemplo, `Esto es un __ejemplo__.` en markdown se convierte en: Esto es un __ejemplo__.
- ~~Rayado:~~ Emplace el texto entre asteriscos. Por ejemplo, `Esto es un ~~ejemplo~~.` en markdown se convierte en: Esto es un ~~ejemplo~~.

# Documentación de Componentes (Markdown)
A continuación, se detalla el listado de componentes que se pueden utilizar para representar una lección.

## 0. Section

**Descripción:** Este componente se utiliza para representar una pantalla completa (sección) en la aplicación. Contiene uno o más grupos de componentes que se mostrarán juntos. Este componente se usa para estructurar el contenido de una lección de forma lógica y manejable, permitiendo dividir el contenido en múltiples pantallas si es necesario.

**Uso:**
Cree una línea que comience con `# Section` y divídalo en grupos y componentes. Se dará por terminada la sección cuando llegue al final del documento o cuando se encuentre con otra línea con `# Section`.

**Ejemplo:**

```markdown
# Section

## Group
...

# Section

## Group
...

## Group
...
```

### Explicación:

Este componente contiene dos secciones. El primero incluye un solo grupo, mientras que el segundo grupo incluye dos grupos.


## 1. Group
El componente group se utiliza para agrupar varios componentes y presentarlos juntos en la pantalla. Una vez completados los ejercicios dentro del grupo, se pueden mostrar los siguientes grupos o componentes.

**Uso:**
Igual que `# Section`.

#### Ejemplo:

```markdown
## Group

### Title
...

### Paragraph
...

## Group

### Paragraph
```

### Explicación:

Este grupo contiene un title y un paragraph. El segundo, solo un párrafo.


## 2. Title

### Descripción:
El componente title se utiliza para mostrar headers o subheaders que separan el contenido dentro de una sección o grupo.

### Uso:
Pon `### Title` para un subtítulo o un `### Title (header)` para *el primer title de la sección*.

### Ejemplo:

```markdown
## Title (header)
Ejemplo de título *(más grande que el siguiente por ser un header)*


## Title
Ejemplo de título (subheader)
```


## 3. Paragraph

### Descripción:
El componente paragraph se utiliza para mostrar párrafos de texto que pueden contener snippets `{SNIPPET}` a completar con opciones. En caso de querer confeccionar una tabla, se habrá de usar un párrafo distinto por cada fila de la misma y adaptar el contenido a una vista de párrafo en lugar de tabla (excluyendo los headers, eliminando algún que otro campo si es necesario, etc.).

### Uso:
Añade un párrafo e inmediatamente después las opciones y los índices para las opciones correctas. No debe añadir `options` y `rightOptions` añadirlo si no se incluye ningún `{SNIPPET}`. Cada párrafo debe estar anidado en un `### Paragraph` aparte. Véase el ejemplo 2 para mayor ilustración: en vez de poner los dos párrafos seguidos, se parten en dos, etiquetando cada uno con `### Paragraph`.

### Ejemplo 1:

```markdown
### Paragraph
En inglés, se hace una distinción entre los pronombres que actúan como {SNIPPET} y los que funcionan como {SNIPPET}.

- Options: [["sujeto", "abstracción"], ["verbo", "objeto"]]
- Right Options: [0, 1]
```

### Ejemplo 2:

```markdown
### Paragraph
En inglés, se hace una distinción entre los pronombres que actúan como sujeto y los que funcionan como objeto.

### Paragraph
En inglés, se hace una distinción entre los pronombres que actúan como {SNIPPET} y los que funcionan como {SNIPPET}.

- Options: [["sujeto", "abstracción"], ["verbo", "objeto"]]
- Right Options: [0, 1]
```

## 4. Example

### Descripción:
El componente example se utiliza para mostrar ejemplos de oraciones en el idioma de aprendizaje con su correspondiente traducción. Estos ejemplos pueden contener snippets `{SNIPPET}` que deben ser completados con opciones.

### Uso:
Añada `### Example` e inmediatamente debajo cree estas estructuras:

#### 1. Si va a hacerlo con opciones (el usuario ha de seleccionar una de las opciones que usted pone)

```markdown
### Example
1. Main Text: `texto en inglés`
   - Sub Text: `texto en español`
   - Options: `arrays de arrays de cadenas de texto json`
   - Right Options: `arrays de números enteros json`
```


#### 2. Si va a hacerlo con valid inputs (se le pide al usuario escribir la respuesta, y usted pone una serie de inputs que se darán como válidos)
```markdown
### Example
1. Main Text: `texto en inglés`
   - Sub Text: `texto en español`
   - Valid Inputs: `arrays arrats de cadenas de texto json`
```


### Ejemplo 1 (con opciones):

```markdown
### Example
1. Main Text: {SNIPPET} am ill. You {SNIPPET} not.
   - Sub Text: Yo estoy enfermo.
   - Options: [["I", "you"], ["are", "is"]]
   - Right Options: [0, 0]

...
```


### Ejemplo 2 (con validInputs):

```markdown
### Example
1. Main Text: {SNIPPET} is handsome.
   - Sub Text: Él es guapo.
   - Valid Inputs: [["he", "that guy"]]

...
```


## 5. Notification

### Descripción:
El componente notification se utiliza para mostrar mensajes informativos al usuario.

### Uso:
Agregue `### Notification` e incluya el texto acto seguido.

### Ejemplo:

```markdown
### Notification
La palabra *will* también puede abreviarse como *'ll*.
```


# Ejemplo JSON vs MD

### Versión JSON
```json
{
    "screens": [
      {
        "type": "section",
        "children": [
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "Pronombres personales",
                "header": true
              },
              
              {
                "type": "paragraph",
                "text": "Dentro de los pronombres personales, <B>la lengua inglesa distingue entre pronombres en función de sujeto</B>  (subject pronouns) <B>y pronombres en función de objeto</B>  (object pronouns)."
                
              },
             
              
              {
                "type": "paragraph",
                "text": "En inglés, se hace una distinción entre los pronombres que actúan como {SNIPPET} y los que funcionan como {SNIPPET}.",
                "options": [
                  ["sujeto", "abstracción"],
                  ["verbo", "objeto"]
                ],
                "rightOptions": [0, 1]
              }
            ]
          },
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "Ejemplos de pronombres(en función de sujeto)",
                "header": false
              },
              {
                "type": "example",
                "children": [
                  {
                    "mainText": "{SNIPPET} am ill.",
                    "subText": "Yo estoy enfermo.",
                    "options": [["I", "You", "He"]],
                    "rightOptions": [0]
                  },
                  {
                    "mainText": "{SNIPPET} are tall.",
                    "subText": "Tú eres alto.",
                    "options": [["I", "You", "He"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "{SNIPPET} is handsome.",
                    "subText": "Él es guapo.",
                    "options": [["I", "You", "He"]],
                    "rightOptions": [2]
                  }
                ]
              }
            ]
          },
          {
            "type": "group",
            "children": [
              
              {
                "type": "example",
                "children": [
                  {
                    "mainText": "{SNIPPET} is pretty.",
                    "subText": "Ella es guapa.",
                    "options": [["I", "She", "He"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "{SNIPPET} is cold today.",
                    "subText": "Hoy hace frío.",
                    "options": [["They", "He", "It"]],
                    "rightOptions": [2]
                  },
                  {
                    "mainText": "{SNIPPET} are tired.",
                    "subText": "Nosotros estamos cansados.",
                    "options": [["You", "We", "They"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "{SNIPPET} are angry.",
                    "subText": "Vosotros estáis enfadados. / Ustedes están enfadados.",
                    "options": [["You", "We", "They"]],
                    "rightOptions": [0]
                  },
                  {
                    "mainText": "{SNIPPET} are at the cinema.",
                    "subText": "Ellos están en el cine.",
                    "options": [["You", "We", "They"]],
                    "rightOptions": [2]
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "section",
        "children": [
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "Pronombres(en función de objeto)",
                "header": false
              },
              {
                "type": "paragraph",
                "text": "Para los pronombres de objeto, se colocan después del {SNIPPET} al que complementan o después de preposiciones como «for», «to», «with» y «at».",
                "options": [
                  ["verbo", "sujeto"]
                ],
                "rightOptions": [0]
              }
            ]
          },
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "Ejemplos de pronombres(en función de objeto)",
                "header": false
              },
              {
                "type": "example",
                "children": [
                  {
                    "mainText": "Can you help {SNIPPET}?",
                    "subText": "¿Puedes ayudarme?",
                    "options": [["me", "him", "us"]],
                    "rightOptions": [0]
                  },
                  {
                    "mainText": "I can help {SNIPPET}.",
                    "subText": "Puedo ayudarte.",
                    "options": [["me", "you", "them"]],
                    "rightOptions": [1]
                  },
                  
                  {
                    "mainText": "Can you see {SNIPPET}?",
                    "subText": "¿Le puedes ver?",
                    "options": [["me", "him", "us"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "Give it to {SNIPPET}.",
                    "subText": "Dáselo a ella.",
                    "options": [["me", "her", "us"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "Give {SNIPPET} a kick .",
                    "subText": "Dale una patada.",
                    "options": [["me", "her", "it"]],
                    "rightOptions": [2]
                  },
                  {
                    "mainText": "Can you see {SNIPPET}?",
                    "subText": "¿Nos puedes ver?",
                    "options": [["me", "him", "us"]],
                    "rightOptions": [2]
                  },
                  {
                    "mainText": "I see {SNIPPET}.",
                    "subText": "Os veo. / Les veo.",
                    "options": [["you", "him", "us"]],
                    "rightOptions": [0]
                  },
                  {
                    "mainText": "He can help {SNIPPET}.",
                    "subText": "Él puede ayudarles.",
                    "options": [["me", "them", "you"]],
                    "rightOptions": [1]
                  }
                  
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "section",
        "children": [
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "Notas adicionales sobre pronombres",
                "header": true
              },
              {
                "type": "notification",
                "text": "<b>Nota: En inglés no existe la forma «usted» o «ustedes» formal.</B> La forma masculina, femenina y neutra son lo mismo, lo único que las diferencia es el género. Además, ten en cuenta que <B> en inglés sólo existe una forma para “tú” y “vosotros”, “you”</B>,excepto en la forma reflexiva que distingue entre el singular (<B>yourself</B>) y plural (<B>yourselves</B>)."
              },
              {
                "type": "paragraph",
                "text": "En inglés sólo existe una forma para «tú», «vosotros» y «usted/es»: {SNIPPET}.",
                "options": [
                  ["you","yourself"]
                ],
                "rightOptions": [0]
              }
              
              
            ]
          },
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "Uso del pronombre «it»",
                "header": false
              },
              
              {
                "type": "paragraph",
                "text": "El pronombre personal «it» se utiliza cuando nos referimos a cosas, a animales que no sabemos su sexo o al tiempo (calendario y meteorológico). La forma plural de {SNIPPET} es «they».",
                "options": [
                  ["it", "you"]
                ],
                "rightOptions": [0]
              },
              {
                "type": "paragraph",
                "text": "El {SNIPPET} «it» se utiliza para referirse a cosas, animales desconocidos y al tiempo.",
                "options": [
                  ["pronombre", "sujeto"]
                ],
                "rightOptions": [0]
              }
              
            ]
          },
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "Ejemplos del pronombre «it»",
                "header": false
              },
              {
                "type": "example",
                "children": [
                  {
                    "mainText": "Where is {SNIPPET} [the book]?",
                    "subText": "¿Dónde está [el libro]?",
                    "options": [["it","that"]],
                    "rightOptions": [0]
                  },
                  {
                    "mainText": "What time is {SNIPPET}?  ",
                    "subText": "¿Qué hora es?",
                    "options": [["it", "this"]],
                    "rightOptions": [0]
                  },
                  {
                    "mainText": "{SNIPPET} is raining.",
                    "subText": "Está lloviendo.",
                    "options": [["It", "They"]],
                    "rightOptions": [0]
                  },
                  
                  {
                    "mainText": " ",
                    "subText": " "
                    
                  },
                  {
                    "mainText": "<B>Nota: «It» es una partícula muy importante en inglés</B> de la que los hablantes de lengua española se suelen olvidar.",
                    "subText": " "
                    
                  }
                  
                  
                ]
              }
            ]
          },
          
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "<B>El pronombre</B> (en función de sujeto)",
                "header": false
              },
              {
                "type": "notification",
                "text": "<B>El sujeto de una oración es la persona o cosa que realiza la acción del verbo.</B>Se utilizan los pronombres en función de sujeto cuando el pronombre es el sujeto de la oración. Este pronombre en inglés, a diferencia del español, <B>debe figurar siempre</B>."
              },
              {
                "type": "notification",
                "text": ""
              },
              {
                "type": "example",
                "children": [
                  {
                    "mainText": "{SNIPPET} am ill.",
                    "subText": "Estoy enfermo.",
                    "options": [["i","me"]],
                    "rightOptions": [0]
                  },
                  {
                    "mainText": "{SNIPPET} are tall.  ",
                    "subText": "Eres alto.",
                    "options": [["they", "you"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "{SNIPPET} is Handsome.",
                    "subText": "És guapo.",
                    "options": [["she", "he"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "{SNIPPET} are tired.",
                    "subText": "Estamos cansados.",
                    "options": [["we", "they"]],
                    "rightOptions": [0]
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "section",
        "children": [
          {
            "type": "group",
            "children": [
              {
                "type": "title",
                "text": "<B>El pronombre</B> (en funcion del objeto)",
                "header": false
              },
              {
                "type": "notification",
                "text": "Este pronombre <b>se coloca a continuación del verbo al que complementa</B> o a continuación de preposiciones como <B>«for»</B>, <B>«to»</B>, <B>«with»</B> y <B>«at»</B>."
              },
               {
                "type": "example",
                "children": [
                  {
                    "mainText": " I can help{SNIPPET}?",
                    "subText": "Puedo ayudarte.",
                    "options": [["it", "you"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "Can you see {SNIPPET}?",
                    "subText": "¿Puedes verle?",
                    "options": [["me", "him"]],
                    "rightOptions": [1]
                  },
                  {
                    "mainText": "He is going to the party with {SNIPPET}.",
                    "subText": "Él va a la fiesta con nosotros.",
                    "options": [[ "us","me"]],
                    "rightOptions": [0]
                  },
                  {
                    "mainText": "It [the letter] is for {SNIPPET}.",
                    "subText": "Es [la carta] para ti.",
                    "options": [["you", "him"]],
                    "rightOptions": [0]
                  }
            ]
          }
         
            ]
          }
        ]
      }
      
    ]
  }
```

### Versión MD
```markdown
# Section

## Group

### Title
**Pronombres personales**

### Paragraph
Dentro de los pronombres personales, **la lengua inglesa distingue entre pronombres en función de sujeto** (subject pronouns) **y pronombres en función de objeto** (object pronouns).

### Paragraph
En inglés, se hace una distinción entre los pronombres que actúan como {SNIPPET} y los que funcionan como {SNIPPET}.

- Options: [["sujeto", "abstracción"], ["verbo", "objeto"]]
- Right Options: [0, 1]

## Group

### Title
Ejemplos de pronombres (en función de sujeto)

### Example
1. Main Text: {SNIPPET} am ill.
   - Sub Text: Yo estoy enfermo.
   - Options: [["I", "You", "He"]]
   - Right Options: [0]

2. Main Text: {SNIPPET} are tall.
   - Sub Text: Tú eres alto.
   - Options: [["I", "You", "He"]]
   - Right Options: [1]

3. Main Text: {SNIPPET} is handsome.
   - Sub Text: Él es guapo.
   - Options: [["I", "You", "He"]]
   - Right Options: [2]

## Group

### Example
1. Main Text: {SNIPPET} is pretty.
   - Sub Text: Ella es guapa.
   - Options: [["I", "She", "He"]]
   - Right Options: [1]

2. Main Text: {SNIPPET} is cold today.
   - Sub Text: Hoy hace frío.
   - Options: [["They", "He", "It"]]
   - Right Options: [2]

3. Main Text: {SNIPPET} are tired.
   - Sub Text: Nosotros estamos cansados.
   - Options: [["You", "We", "They"]]
   - Right Options: [1]

4. Main Text: {SNIPPET} are angry.
   - Sub Text: Vosotros estáis enfadados. / Ustedes están enfadados.
   - Options: [["You", "We", "They"]]
   - Right Options: [0]

5. Main Text: {SNIPPET} are at the cinema.
   - Sub Text: Ellos están en el cine.
   - Options: [["You", "We", "They"]]
   - Right Options: [2]


# Section

## Group

### Title
Pronombres (en función de objeto)

### Paragraph
Para los pronombres de objeto, se colocan después del {SNIPPET} al que complementan o después de preposiciones como «for», «to», «with» y «at».

- Options: [["verbo", "sujeto"]]
- Right Options: [0]

## Group

### Title
Ejemplos de pronombres (en función de objeto)

### Example
1. Main Text: Can you help {SNIPPET}?
   - Sub Text: ¿Puedes ayudarme?
   - Options: [["me", "him", "us"]]
   - Right Options: [0]

2. Main Text: I can help {SNIPPET}.
   - Sub Text: Puedo ayudarte.
   - Options: [["me", "you", "them"]]
   - Right Options: [1]

3. Main Text: Can you see {SNIPPET}?
   - Sub Text: ¿Le puedes ver?
   - Options: [["me", "him", "us"]]
   - Right Options: [1]

4. Main Text: Give it to {SNIPPET}.
   - Sub Text: Dáselo a ella.
   - Options: [["me", "her", "us"]]
   - Right Options: [1]

5. Main Text: Give {SNIPPET} a kick.
   - Sub Text: Dale una patada.
   - Options: [["me", "her", "it"]]
   - Right Options: [2]

6. Main Text: Can you see {SNIPPET}?
   - Sub Text: ¿Nos puedes ver?
   - Options: [["me", "him", "us"]]
   - Right Options: [2]

7. Main Text: I see {SNIPPET}.
   - Sub Text: Os veo. / Les veo.
   - Options: [["you", "him", "us"]]
   - Right Options: [0]

8. Main Text: He can help {SNIPPET}.
   - Sub Text: Él puede ayudarles.
   - Options: [["me", "them", "you"]]
   - Right Options: [1]


# Section

## Group

### Title
Notas adicionales sobre pronombres

### Notification
**Nota: En inglés no existe la forma «usted» o «ustedes» formal.** La forma masculina, femenina y neutra son lo mismo, lo único que las diferencia es el género. Además, ten en cuenta que **en inglés sólo existe una forma para “tú” y “vosotros”, “you”**, excepto en la forma reflexiva que distingue entre el singular (**yourself**) y plural (**yourselves**).

### Paragraph
En inglés sólo existe una forma para «tú», «vosotros» y «usted/es»: {SNIPPET}.

- Options: [["you","yourself"]]
- Right Options: [0]

## Group

### Title
Uso del pronombre «it»

### Paragraph
El pronombre personal «it» se utiliza cuando nos referimos a cosas, a animales que no sabemos su sexo o al tiempo (calendario y meteorológico). La forma plural de {SNIPPET} es «they».

- Options: [["it", "you"]]
- Right Options: [0]

### Paragraph
El {SNIPPET} «it» se utiliza para referirse a cosas, animales desconocidos y al tiempo.

- Options: [["pronombre", "sujeto"]]
- Right Options: [0]

## Group

### Title
Ejemplos del pronombre «it»

### Example
1. Main Text: Where is {SNIPPET} [the book]?
   - Sub Text: ¿Dónde está [el libro]?
   - Options: [["it","that"]]
   - Right Options: [0]

2. Main Text: What time is {SNIPPET}?
   - Sub Text: ¿Qué hora es?
   - Options: [["it", "this"]]
   - Right Options: [0]

3. Main Text: {SNIPPET} is raining.
   - Sub Text: Está lloviendo.
   - Options: [["It", "They"]]
   - Right Options: [0]

### Notification
**Nota: «It» es una partícula muy importante en inglés** de la que los hablantes de lengua española se suelen olvidar.


# Section

## Group

### Title
**El pronombre** (en función de sujeto)

### Notification
**El sujeto de una oración es la persona o cosa que realiza la acción del verbo.** Se utilizan los pronombres en función de sujeto cuando el pronombre es el sujeto de la oración. Este pronombre en inglés, a diferencia del español, **debe figurar siempre**.

### Example
1. Main Text: {SNIPPET} am ill.
   - Sub Text: Estoy enfermo.
   - Options: [["i","me"]]
   - Right Options: [0]

2. Main Text: {SNIPPET} are tall.
   - Sub Text: Eres alto.
   - Options: [["they", "you"]]
   - Right Options: [1]

3. Main Text: {SNIPPET} is Handsome.
   - Sub Text: És guapo.
   - Options: [["she", "he"]]
   - Right Options: [1]

4. Main Text: {SNIPPET} are tired.
   - Sub Text: Estamos cansados.
   - Options: [["we", "they"]]
   - Right Options: [0]


# Section

## Group

### Title
**El pronombre** (en funcion del objeto)

### Notification
Este pronombre **se coloca a continuación del verbo al que complementa** o a continuación de preposiciones como **«for»**, **«to»**, **«with»** y **«at»**.

### Example
1. Main Text: I can help{SNIPPET}.
   - Sub Text: Puedo ayudarte.
   - Options: [["it", "you"]]
   - Right Options: [1]

2. Main Text: Can you see {SNIPPET}?
   - Sub Text: ¿Puedes verle?
   - Options: [["me", "him"]]
   - Right Options: [1]

3. Main Text: He is going to the party with {SNIPPET}.
   - Sub Text: Él va a la fiesta con nosotros.
   - Options: [["us", "me"]]
   - Right Options: [0]

4. Main Text: It [the letter] is for {SNIPPET}.
   - Sub Text: Es [la carta] para ti.
   - Options: [["you", "him"]]
   - Right Options: [0]
```
