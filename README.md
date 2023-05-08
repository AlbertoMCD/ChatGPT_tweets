# Tweets sobre ChatGPT

Repositorio para proyecto final de la materia Desarrollo de Proyecto II, realizado por Mauricio Arnoldo Tenorio Vargas y Alberto Martínez Lara.

El objetivo del presente proyecto es analizar la opinión pública en Twitter sobre el sistema de chatbot IA ChatGPT.

![](https://media.giphy.com/media/SnbwVKTj0vBQSK47us/giphy.gif)

Fuente: [Giphy](https://media.giphy.com/media/SnbwVKTj0vBQSK47us/giphy.gif)

La estructura de este repositorio sigue prácticas recomendadas de acuerdo al paper ["Good Enough Practices in Scientific Computing"](https://arxiv.org/abs/1609.00037) por Greg Wilson, Jennifer Bryan, Karen Cranston, Justin Kitzes, Lex Nederbragt, Tracy K. Teal.

    ├── LICENSE           <- MIT License.  
    |  
    ├── README.md         <- Archivo Readme principal con la descripción y resultados principales del proyecto.  
    |  
    ├── CONTRIBUTING.md   <- Notas sobre contribuciones al proyecto.  
    |  
    ├── CITATION.md       <- Forma de citar el proyecto.  
    |  
    ├── data              <- Base de datos de origen.  
    |  
    ├── doc               <- Archivos de texto.  
    |  
    ├── results           <- Resultados del proyecto: datos procesados, gráficos, etc.  
    |  
    └── src               <- Archivos de código.  

## Introducción

ChatGPT es un modelo de de Machine Learning desarrollado por OpenAI, que utiliza la arquitectura GPT (Generative Pre-trained Transformer). Su propósito es entablar conversaciones en lenguaje natural con humanos a traez de consultas o en ingles (prompts).

Como modelo de lenguaje, ChatGPT ha sido entrenado en una gran cantidad de datos de texto de Internet, lo que le permite generar matrizes de lenguaje extremadamente complejas y eficacez, logrando proveer de información al usuario de manera rapida y personalizada basandose en el modelo asi como los promts previamente enviados por el usuario, lo cual ah hecho que el modelo sea sumamente poderoso e inquietante.

Dicho lo anterior, ChatGPT es una herramienta que genera entusiasmo y para lgunas personas y organizaciones, tambien preocupacion. El modelo ya se ah usado para difundir desinformaicion, obtener informacion privada prviamente alimantada por el algoritmo, uso poco etico en instituciones educativas, etc.


## Objetivo
![](https://aijn.eu/files/attachments/.113/w500h300q85_Target.png?1547139106631)
Fuente: [Aijin](https://aijn.eu/files/attachments/.113/w500h300q85_Target.png?1547139106631)

El objetivo del projeto es comprender con mayor detalle el sentimiento y la percepcion del publico en general acerca de ChatGPT, utilizando herramientas utilizadas en la materia de Desarrollo de Proyectos. 

Para lograr el objetivo utilizamos las siguientas herramientas y librerias para el projecto.


### Herramientas para el Proyecto

**Lenguaje/Plataforma**
* [Jupyter Notebooks](https://jupyter.org/)

**Librerías**
* [Numpy](https://numpy.org/)
* [Pandas](https://pandas.pydata.org/)
* [Altair](https://altair-viz.github.io/)
* [Scipy](https://scipy.org/)
* [nltk](https://www.nltk.org/)


## Resultados

Los Resultados exportables se pueden descargar del siguiente [enlace](https://github.com/m5991/tecnologiaMexico/tree/main/results).

Estructura del [Notebook](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/src/ChatGPT%20Tweets%20Analysis.ipynb) es la siguiente:

1. Información del Dataset
2. Limpieza de Datos
3. EDA
4. Procesamiento de texto
5. Análisis de sentimiento



### Informacion del Dataset

Queremos agradecer a [Eduardo Rios](https://github.com/edurios2021), por ayudarnos a utilizar su cuenta activa con el API de twitter para asi obtener los 3000 tweets utilizando la libreria Tweepy.

Las variables screapeads con Tweepy  en un intervalo de 2 horas conteniendo la palabra ChatGPT son las siguientes:

* text: Contenido del tweet.
* favorited: Estado binario de si fue agregado como favorito el tweet
* favoriteCount: Conteo de veces que el tweet fue marcado con favorito por otro usuario.
* replyToSN: Contenido del tweet.
* created: Fecha, hora y minuto de creación del tweet.
* truncated: Indicador de si el Tweet fue truncado al momento de obtenerlo con el API.
* replyToSID: NA
* id: Identificador del tweet.
* replyToUID: NA
* statusSource: html source.
* screenName: Usuario.
* retweetCount: Numero de retweets.
* isRetweet: Indicador de si el tweet es un Retweet o Tweet regular..
* retweeted: Indicador de si el tweet fue retweeteado.
* longitude: longitud del origen del tweet.
* latitude: latitud del origen del tweet.




### Limpieza de Datos

El dataset general se eonctraba listo para en analisis, solo realizamos algunas trasformaciones y eleminamos columnas inncesarias para el analisis

```
df = df.drop(['replyToSID', 'id', 'replyToUID', 'longitude', 'latitude', 'replyToSN'], axis=1)
```


### EDA

[Created Hour Bar Plot](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/CreatedHour.png)

Aproximadamente el 90% de los tweets scrapeados fueron a las 5 de la tarde, el resto fue alrededor de las 4.


[Source Distribution](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/statusSource.png)


### Procesamiento de Texto