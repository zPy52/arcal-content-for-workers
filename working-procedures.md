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

## 1. Leer el contenido en las carpetas y en curso-ingles.com

Se recomienda leer *primero* el contenido de curso-ingles.com y *luego* el que se dispone en los archivos `.json`. De esta manera, las deficiencias del payload JSON saldrán a la vista. La idea de este paso es hacerse una idea general de qué va la lección y qué le falta o qué se puede mejorar en el payload JSON.

## 2. Ir componente por componente leyendo y actualizando

Ha de irse componente por componente en el archivo `.json` leyéndolo detenidamente y comparándolo con la web curso-ingles.com. Nótese cómo ha de (1) leer el componente; (2) leer la parte correspondiente/de donde se extrajo en curso-ingles.com; y (3) corregirlo en base a ello. 

Es muy importante este orden, aunque más tedioso, de ir (1) componente -> (2) web -> (3) componente. Solo ello puede garantizar una calidad adecuada en el resultado final. Léase [Ciertos errores a evitar](https://github.com/zPy52/arcal-content-for-workers/blob/main/errors-to-elude.md) y la [Documentación de Componentes](https://github.com/zPy52/arcal-content-for-workers/blob/main/components.md) para conocer más detalles sobre qué cambios aplicar al payload.

## 3. Revisar

Una vez se haya ido por todos los componentes aplicando el paso 2, se ha de repetir el proceso volviendo al inicio (al primer componente) y realizando, de nuevo, exactamente el mismo proceso: (1) componente -> (2) web -> (3) componente. Tras revisar el componente, se pasa al siguiente.

*Si se ha hecho algún cambio*, se ha de repetir, de nuevo, todo el proceso: **se vuelve al primer componente** y se va bajando a partir de ahí. Si no se ha aplicado ningún cambio, se pasa a la siguiente lección o unidad.
