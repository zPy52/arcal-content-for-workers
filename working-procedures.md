# Procedimientos de trabajo para lecciones gramaticales

Buscamos preparar a nuestros estudiantes de idiomas para dominar la lengua para la que se preparan (alcanzar el C2 en el Marco Común Europeo de Referencia para las Lenguas). Consideramos como nuestro trabajo el reducir (1) el esfuerzo; y (2) tiempo que toma a los estudiantes estudiar y llegar ese nivel.

Con ello en mente, se especifica el siguiente procedimiento de trabajo para la creación de ejercicios gramaticales expresados en payloads JSON.

## 0. Leer el payload y abrir el contenido en curso-ingles.com

ChatGPT ha creado para nosotros los payloads que le enviamos en carpetas. El trabajo consiste en pulir las deficiencias del mismo, principalmente que (1) el Chat a veces no incluye todo el contenido de la lección de curso-ingles.com; y (2) las opciones de los snippets de los ejemplos/párrafos que pone son mejorables. (Léase [Documentación de Componentes](https://github.com/zPy52/arcal-content-for-workers/blob/main/components.md) para indagar en qué es un snippet, qué es un párrafo o un ejemplo).

Esta es la estructura de carpetas:

![estructura de carpetas](https://i.imgur.com/N2JEjKx.png)


Hay tres carpetas superiores: `nivel-basico`, `nivel-intermedio` y `nivel-avanzado`. Cada uno corresponde a un curso en curso-ingles.com. En cada uno de estos niveles se encuentran las unidades (como `christmas` en `nivel-basico`). Y dentro de estas, se encuentran archivos `.json` con el contenido de cada lección, que corresponden a cada lección de la unidad correspondiente en curso-ingles.com. La url de cada lección es:

```
https://www.curso-ingles.com/aprender/cursos/{nivel}/{unidad}/{lección}
```

Por ejemplo, para la lección `christmas-vocabulary` de la unidad `christmas` del `nivel-basico`, la url es:

```
https://www.curso-ingles.com/aprender/cursos/nivel-basico/christmas/christmas-vocabulary
```


## 1. Ver el contenido en curso-ingles.com

