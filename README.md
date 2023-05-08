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

![Created Hour Bar Plot](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/CreatedHour.png)

Aproximadamente el 90% de los tweets scrapeados fueron a las 5 de la tarde, el resto fue alrededor de las 4.


![Source Distribution](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/statusSource.png)

Las principales plataformas de origen de los tweets son Android, iOS y WebApp, es interesante que Android y iOS estan sumamente parejos, posiblmente no se obtenga el mismo resultado si se scrapena tweets unicamente de USA.


### Procesamiento de Texto

Debido a las restricciones del scraper, obtenemos tweets globales, por lo que obtamos por utilizar una libreria prenetrenada para detectar el lenguaje utilizando el siguiente codigo: 


```

from langdetect import detect

for index, row in df_texto['text'].iteritems():
    try:
        lang = detect(row) #detecting each row
        df_texto.loc[index, 'idioma'] = lang
    except:
        continue

df_texto
```

Par aposteriormente traducirlo con la la libreria [deep_translator](https://pypi.org/project/deep-translator/)

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/translated%20tweets.png)



Postoriormente se realizaron transofrmaciones utilizando python y librerias externas para eliminar signos de puntuacion, cambiar texto a minúsculas, tokenización, stopwords, Lematización y extracción de urls para obtener finalmente la columna text_clean con el texto 'limpio'

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/text_clean.png)


### Análisis de sentimiento


Para generar el analisis de sentimiento utilizamos utilizando el nuevo dataframe limpio utilizamos la siguiente funcion:

```

# Añadir análisis de sentimiento
nlp.add_pipe("spacytextblob")

df_sent = pd.DataFrame()

for i in range(len(df_texto)):
    doc = nlp(df_texto.iloc[i]['text_clean'])
    idioma = df_texto.iloc[i]['idioma']
    df_1 = pd.DataFrame({
        "clean_tweet":doc.text,
        "polarity":doc._.blob.polarity,
        "subjectivity":doc._.blob.subjectivity,
        "language":idioma
    }, index=[0])
    df_sent = pd.concat([df_sent, df_1])
    
df_sent
```
#### Polaridad
De esta manera obtuvimos los siguientes graficos con las nuevas variables de Polaridad y Subjetividad:

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Polaridad.png)

Se observa una distribucion relativamente normal, la mayor cantidad de tweets tine una polaridad Neutra.

#### Subjetividad

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Subjetividad.png)

En el caso de la subjetividad del sentimiento la distribucion se observa relativamente plana, aunque tomando en cuenta que el valor de la frecuencia no es lineal, la cantidad de tweets con muy poca subjetividad (0 - 0.10) es alta, pracaticamente 1/3 de los tweets.

#### Subjetividad vs Polaridad
![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Polaridad.png)

El diagrama de dispersion de ambas variables muestra buena variacion entre las varialbes y cierta correlacion, entre mayor grado de Polaridad y Subjetividad.



#### Distribucion de los Idiomas


Lenguage Pie Chart
![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Language.png)

La mayoria de los tweets son en ingles, seguido del español.



#### Nube de Palabras

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Nube%20de%20palabras.png)

Las Palabras mas utilizadas como resultado final de nuestro analisis, otraas palabras importantes ademas de chatgpt son: AI, PROMPT, COURSE y OPENAI.







