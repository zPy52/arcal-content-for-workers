Sure, here's your original document altered to an equivalent markdown format:

#####
# Documentación de Componentes
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
