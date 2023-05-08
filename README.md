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

ChatGPT es un modelo de de Machine Learning desarrollado por OpenAI, que utiliza la arquitectura GPT (Generative Pre-trained Transformer). Su propósito es entablar conversaciones en lenguaje natural con humanos a través de consultas o en inglés "prompts".

Como modelo de lenguaje, ChatGPT ha sido entrenado con una gran cantidad de datos de texto de Internet, lo que le permite generar matrizes de lenguaje extremadamente complejas y eficaces, logrando proveer de información al usuario de manera rápida y personalizada, basándose en el modelo, así como los prompts previamente enviados por el usuario, lo cual ha hecho que el modelo sea sumamente poderoso e inquietante.

Dicho lo anterior, ChatGPT es una herramienta que genera entusiasmo y para algunas personas y organizaciones, también preocupación. El modelo ya se ha usado para difundir desinformación, obtener información privada previamente alimentada por el algoritmo, uso poco ético en instituciones educativas, etc.


## Objetivo
![](https://aijn.eu/files/attachments/.113/w500h300q85_Target.png?1547139106631)
Fuente: [Aijin](https://aijn.eu/files/attachments/.113/w500h300q85_Target.png?1547139106631)

El objetivo del proyecto es comprender con mayor detalle el sentimiento y la percepción del público en general acerca de ChatGPT, utilizando herramientas utilizadas en la materia de Desarrollo de Proyectos II. 

Para lograr el objetivo utilizamos las siguientas herramientas y librerías para el proyecto.


### Herramientas para el Proyecto

**Lenguaje/Plataforma**
* [Jupyter Notebooks](https://jupyter.org/)

**Librerías**
* [Numpy](https://numpy.org/)
* [Pandas](https://pandas.pydata.org/)
* [Altair](https://altair-viz.github.io/)
* [Scipy](https://scipy.org/)
* [nltk](https://www.nltk.org/)
* [spacy](https://spacy.io)
* [wordcloud](https://pypi.org/project/wordcloud/)


## Resultados

Difusión en LinkedIn por [Alberto Martínez](https://www.linkedin.com/posts/alberto-mart%C3%ADnez-lara-a87528107_github-albertomcdchatgpttweets-activity-7061204479957729281-gotH?utm_source=share&utm_medium=member_desktop) y [Mauricio Tenorio](https://www.linkedin.com/posts/mauricioten_github-albertomcdchatgpttweets-activity-7061205808843272192-I3_h?utm_source=share&utm_medium=member_desktop).

El detalle de resultados se puede consultar [aquí](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/ChatGPT%20Tweets%20Analysis.md) y el notebook con todo el procedimiento y los resultados se puede consultar [aquí](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/src/ChatGPT%20Tweets%20Analysis.ipynb). 

La estructura del Notebook es la siguiente:

1. Información del Dataset
2. Limpieza de Datos
3. EDA
4. Procesamiento de texto
5. Análisis de sentimiento


### Información del Dataset

Queremos agradecer a [Eduardo Ríos Luna](https://github.com/edurios2021), por ayudarnos a utilizar su cuenta activa con el API de Twitter, para obtener los 3000 tweets, utilizando la libreria Tweepy.

Las variables scrapeadas con Tweepy  en un intervalo de 2 horas conteniendo la palabra ChatGPT son las siguientes:

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
* isRetweet: Indicador de si el tweet es un Retweet o Tweet regular.
* retweeted: Indicador de si el tweet fue retweeteado.
* longitude: longitud de la ubicación origen del tweet.
* latitude: latitud de la ubicación origen del tweet.




### Limpieza de Datos

El dataset general se encontraba listo para el análisis, se realizaron pocas trasformaciones y se eliminaron columnas innecesarias para el análisis.

```
df = df.drop(['replyToSID', 'id', 'replyToUID', 'longitude', 'latitude', 'replyToSN'], axis=1)
```


### EDA

![Created Hour Bar Plot](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/CreatedHour.png)

Aproximadamente el 90% de los tweets fueron obtenidos a las 5 de la tarde, el resto fueron alrededor de las 4.


![Source Distribution](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/statusSource.png)

Las principales plataformas de origen de los tweets son Android, iOS y WebApp, es interesante observar que Android y iOS están sumamente parejos, posiblemente no se obtenga el mismo resultado si se scrapean tweets únicamente de USA.


### Procesamiento de Texto

Debido a las restricciones del scraper, obtenemos tweets globales, por lo que optamos por utilizar una librería preentrenada para detectar el lenguaje utilizando el siguiente código: 


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

Posteriormente, se realizó la traducción con la librería [deep_translator](https://pypi.org/project/deep-translator/).

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/translated%20tweets.png)



Se realizaron transformaciones utilizando Python y librerías externas para eliminar signos de puntuación, cambiar texto a minúsculas, tokenización, stopwords, lematización y extracción de URL's para obtener finalmente la columna text_clean con el texto 'limpio'.

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/text_clean.png)


### Análisis de sentimiento


Para generar el análisis de sentimiento, se empleó el nuevo dataframe limpio, y se utilizaron las siguientes funciones:

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
De esta manera obtuvimos las nuevas variables de Polaridad y Subjetividad, que indican el nivel de positividad o negatividad del comentario, así como la objetividad del mismo.

#### Polaridad

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Polaridad.png)

Se observa una distribución relativamente normal, la mayor cantidad de tweets tiene una polaridad neutra cercana a cero.

#### Subjetividad

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Subjetividad.png)

En el caso de la subjetividad, la distribución se observa relativamente plana, aunque tomando en cuenta que la escala de la frecuencia no es lineal, la cantidad de tweets con muy poca subjetividad (0 - 0.10) es alta, prácticamente una tercera parte de los tweets.

#### Subjetividad vs Polaridad
![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Polaridad%20vs%20Subjetividad.png)

El diagrama de dispersión de ambas variables muestra cierta correlacion: a mayor subjetividad, los comentarios tienden a una mayor polaridad, mientras que opiniones más 'objetivas' mantienen una polaridad cercana a cero. 

Por tanto, parece que, si bien hay una discrepancia en opiniones, no existe un sesgo diferencial sobre la opinión analizada, pero sí se aprecia una mayor cantidad de opiniones en el sector positivo.



#### Distribución de los idiomas

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Language.png)

La mayoría de los tweets son en inglés, por lo que provienen de países como E.U., U.K., etc. En segundo lugar, provienen de países de habla hispana (español) y en tercer lugar, provienen de japoneses.



#### Nube de palabras

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Nube%20de%20palabras.png)

En este wordcloud, se muestran las palabras más utilizadas como resultado final de nuestro análisis. Además de Chatgpt, otras palabras que se destacan entre los tweets son: AI, PROMPT, COURSE y OPENAI.