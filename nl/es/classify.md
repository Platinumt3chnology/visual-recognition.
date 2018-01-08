---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-30"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Acerca de los clasificadores

Cuando se clasifica una imagen, Visual Recognition devuelve un conjunto de clases encontradas en la imagen. Obtiene dicha información de las imágenes sobre las que está entrenado. Un clasificador es un grupo de clases.

Visual Recognition incluye varios clasificadores incorporados que pueden proporcionar resultados muy precisos sin la necesidad de realizar el entrenamiento. También puede entrenar a clasificadores personalizados para crear clases especializadas.

Iniciación a Clarifai
> El tipo de predicción se basa en el modelo a través del que ejecuta la entrada. Por ejemplo, si se ejecuta la entrada a través del modelo 'food', las predicciones que devuelve contendrán conceptos que el modelo 'food' conoce. Si ejecuta la entrada a través del modelo 'color', devolverá predicciones sobre los colores dominantes en la imagen.

Clarifai
> Clarifai proporciona muchos modelos distintos que 'ven' el mundo diferente. Un modelo contiene un grupo de conceptos. Un modelo sólo verá los conceptos que contiene.
>
> Hay veces que deseará tener un modelo que vea el mundo de la misma forma que usted. La API le permite hacerlo. Puede crear su propio modelo y entrenarlo con sus propias imágenes y conceptos. Una vez entrenado para que vea como le gustaría que viese, puede utilizar ese modelo para hacer predicciones.

## Clasificadores incorporados

Visual Recognition incluye un conjunto de clasificadores que proporcionan resultados muy precisos sin entrenamiento. Los clasificadores actuales incorporados se denominan `default`, `food` y `explicit`.

### Clasificador default

El clasificador default devuelve clases de miles de etiquetas posibles organizadas en categorías y subcategorías. Se pueden devolver las siguientes categorías de nivel superior:

- Animales (como aves, reptiles, anfibios, etc.)
- Información y actividades orientadas a personas
- Alimentos (incluidas bebidas y alimentos procesados)
- Plantas (incluidos árboles, arbustos, plantas acuáticas, verduras)
- Deportes
- Naturaleza (incluidos muchos tipos de formaciones naturales, estructuras geológicas)
- Transporte (tierra, agua, aire)
- Y muchas más, incluidos muebles, frutas, instrumentos musicales, herramientas, colores, gadgets, dispositivos, instrumentos, armas, edificios, estructuras y objetos artificiales, ropa y prendas de vestir, y flores, entre otras.

### Clasificador food

Aunque el clasificador default puede identificar alimentos y bebidas, puede especificar el clasificador `food` incorporado para...

### Clasificador explicit

Visual Recognition puede clasificar si una imagen es inapropiada para el uso general. El clasificador `explicit` actualmente identifica lo que podrían considerarse imágenes pornográficas. Una abreviatura común para esta clasificación es _NSFW_, que significa _no es apropiado para el trabajo_.

Una puntuación por encima o por debajo de un cierto número no es una garantía de que la imagen sea explícita o no. Sin embargo, puede utilizar la respuesta como filtro inicial de una imagen, y analizarla más a partir de ahí.

Respuesta:
```json
{
  "images": [
    {
      "classifiers": [
        {
          "classes": [
            {
              "class": "not explicit",
              "score": 0.704
            }
          ],
          "classifier_id": "explicit",
          "name": "explicit"
        }
      ],
      "resolved_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png",
      "source_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png"
    }
  ],
  "images_processed": 1
}
```
{: codeblock}

## Combinación de clasificadores


## Jerarquía de clases en la respuesta

El método `/v3/classify` clasifica imágenes dentro de una jerarquía de clases relacionadas. Por ejemplo, una imagen de un Beagle podría clasificarse como "animal", así como con las clases relacionadas "dog" y "beagle". Una coincidencia positiva con las clases relacionadas, en este caso "dog" y "beagle", aumenta la puntuación de la respuesta padre. En este ejemplo, la respuesta incluye las tres clases: "animal", "dog" y "beagle". La puntuación de la clase padre ("animal") aumenta porque coincide con las clases relacionadas ("dog" y "beagle"). El padre también es "type\_hierarchy" para mostrar que es padre de la jerarquía.

## Directrices para clasificar grandes volúmenes

Maximice la eficiencia y el rendimiento del servicio de las siguientes maneras cuando envíe muchas imágenes:

- Recorte o redimensione las imágenes a 224 x 224 píxeles. El servicio está actualmente optimizado para este tamaño, aunque podría cambiar.
    - Recorte la imagen si tiene una proporción de aspecto superior a 2:1 o inferior a 1:2.
    - Considere recortar la imagen en varias imágenes cuadradas, o incluir sólo el centro de la imagen, en función de lo que sea más importante para su uso.
- Envíe hasta 20 imágenes en un único archivo .zip. No es necesario utilizar ninguna compresión, porque las imágenes JPEG y PNG son archivos comprimidos.
- Utilice el parámetro **classifier_ids** para especificar sólo los clasificadores que desea utilizar.
- Aunque el servicio lee etiquetas EXIF y gira imágenes, para un mejor rendimiento, envíe imágenes que no sea necesario que gire el servicio (la etiqueta **Orientation** EXIF definida en `1`).
