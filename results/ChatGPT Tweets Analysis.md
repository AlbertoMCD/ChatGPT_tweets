<p align="center">
  <img width="550" height="281" src="http://encuentratubeca.mx/wp-content/uploads/2019/04/logoudgvectores_1_origsdaasss.png">
</p>

# <center>Proyecto Final de la materia Desarrollo de Proyecto II</center>             
------
## Maestría en Ciencia de los Datos
#### Alberto Martínez Lara
#### Mauricio Arnoldo Tenorio Vargas

#### Mayo 2023

## Introducción

ChatGPT es un modelo de de Machine Learning desarrollado por OpenAI, que utiliza la arquitectura GPT (Generative Pre-trained Transformer). Su propósito es entablar conversaciones en lenguaje natural con humanos a través de consultas o en inglés "prompts".

Como modelo de lenguaje, ChatGPT ha sido entrenado con una gran cantidad de datos de texto de Internet, lo que le permite generar matrizes de lenguaje extremadamente complejas y eficaces, logrando proveer de información al usuario de manera rápida y personalizada, basándose en el modelo, así como los prompts previamente enviados por el usuario, lo cual ha hecho que el modelo sea sumamente poderoso e inquietante.

Dicho lo anterior, ChatGPT es una herramienta que genera entusiasmo y para algunas personas y organizaciones, también preocupación. El modelo ya se ha usado para difundir desinformación, obtener información privada previamente alimentada por el algoritmo, uso poco ético en instituciones educativas, etc.

## Objetivo

El objetivo del proyecto es comprender con mayor detalle el sentimiento y la percepción del público en general acerca de ChatGPT, utilizando herramientas utilizadas en la materia de Desarrollo de Proyectos II. 

Para lograr el objetivo utilizamos las siguientas herramientas y librerías para el proyecto.

#### Informacion del Dataset
Dataset utilizando 

Variables:

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


<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>text</th>
      <th>favorited</th>
      <th>favoriteCount</th>
      <th>replyToSN</th>
      <th>created</th>
      <th>truncated</th>
      <th>replyToSID</th>
      <th>id</th>
      <th>replyToUID</th>
      <th>statusSource</th>
      <th>screenName</th>
      <th>retweetCount</th>
      <th>isRetweet</th>
      <th>retweeted</th>
      <th>longitude</th>
      <th>latitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>RT @gdb: ChatGPT as a tool for Congress: https...</td>
      <td>False</td>
      <td>0</td>
      <td>NaN</td>
      <td>4/27/2023 17:35:29</td>
      <td>False</td>
      <td>NaN</td>
      <td>1651641228520194048</td>
      <td>NaN</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>nos_ult</td>
      <td>58</td>
      <td>True</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>RT @gdb: ChatGPT as a tool for Congress: https...</td>
      <td>False</td>
      <td>0</td>
      <td>NaN</td>
      <td>4/27/2023 17:35:28</td>
      <td>False</td>
      <td>NaN</td>
      <td>1651641223428317185</td>
      <td>NaN</td>
      <td>&lt;a href="http://twitter.com/download/android" ...</td>
      <td>verobouvier</td>
      <td>58</td>
      <td>True</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>RT @moemicky18: So chatgpt failed an accountin...</td>
      <td>False</td>
      <td>0</td>
      <td>NaN</td>
      <td>4/27/2023 17:35:27</td>
      <td>False</td>
      <td>NaN</td>
      <td>1651641221893308416</td>
      <td>NaN</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>uzayrmug</td>
      <td>2</td>
      <td>True</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>RT @JeanPROFITbiz: Les gens gagnent des millie...</td>
      <td>False</td>
      <td>0</td>
      <td>NaN</td>
      <td>4/27/2023 17:35:27</td>
      <td>False</td>
      <td>NaN</td>
      <td>1651641218059608094</td>
      <td>NaN</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>SachaMery</td>
      <td>359</td>
      <td>True</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>does chatgpt mean I, as a wet lab biologist wh...</td>
      <td>False</td>
      <td>0</td>
      <td>NaN</td>
      <td>4/27/2023 17:35:26</td>
      <td>True</td>
      <td>NaN</td>
      <td>1651641214557364234</td>
      <td>NaN</td>
      <td>&lt;a href="http://twitter.com/download/android" ...</td>
      <td>ruth_hook_</td>
      <td>0</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




### EDA 

Distribución por 'Hour created'
    
![Created Hour Bar Plot](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/CreatedHour.png)
    
Se observa que, dado que la extracción de datos se realizó en dos etapas, existen sólo dos horas de creación para los tweets extraídos.


### Status Source distribution

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>statusSource</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Twitter for Android</td>
      <td>951</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Twitter for iPhone</td>
      <td>849</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Twitter Web App</td>
      <td>841</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Twitter for iPad</td>
      <td>44</td>
    </tr>
    <tr>
      <th>4</th>
      <td>TweetDeck</td>
      <td>32</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Buffer</td>
      <td>23</td>
    </tr>
    <tr>
      <th>6</th>
      <td>IFTTT</td>
      <td>22</td>
    </tr>
    <tr>
      <th>7</th>
      <td>dlvr.it</td>
      <td>22</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Twitter for Mac</td>
      <td>19</td>
    </tr>
    <tr>
      <th>9</th>
      <td>LinkedIn</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>

![Source Distribution](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/statusSource.png)

Se aprecia que las principales fuentes de tweets provienen de:
1. Android
2. iPhone
3. Web App
4. iPad
5. TweetDeck
6. Buffer
7. IFTTT
8. dlvr.it
9. Mac
10. LinkedIn

Es interesante observar que Android y iOS están sumamente parejos, posiblemente no se obtenga el mismo resultado si se scrapean tweets únicamente de USA. Asimismo, gran parte de los tweets provienen de la aplicación web de Twitter.

### Resultado final preprocesamiento

Al texto de cada uno de los tweets fue sometido a los siguientes pasos:

1. Detección de idioma
2. Traducción al inglés
3. Eliminar signos de puntuación
4. Cambiar a minúsculas
5. Tokenización
6. Eliminación de stopwords
7. Lematización
8. Eliminación de URL's

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>text</th>
      <th>text_clean</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>RT @gdb: ChatGPT as a tool for Congress: https...</td>
      <td>[rt, @gdb, chatgpt, tool, congress]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>RT @gdb: ChatGPT as a tool for Congress: https...</td>
      <td>[rt, @gdb, chatgpt, tool, congress]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>RT @moemicky18: So chatgpt failed an accountin...</td>
      <td>[rt, @moemicky18, chatgpt, failed, accounting,...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>RT @JeanPROFITbiz: Les gens gagnent des millie...</td>
      <td>[rt, @jeanprofitbiz, people, making, thousand,...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>does chatgpt mean I, as a wet lab biologist wh...</td>
      <td>[chatgpt, mean, wet, lab, biologist, frankenst...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2995</th>
      <td>RT @arabtribunenews: د. فراس الحربي يكتب: ثورة...</td>
      <td>[rt, @arabtribunenews, dr, firas, alharbi, wri...</td>
    </tr>
    <tr>
      <th>2996</th>
      <td>I actually had to redo this one twice because ...</td>
      <td>[actually, redo, one, twice, chatgpt, kept, gi...</td>
    </tr>
    <tr>
      <th>2997</th>
      <td>RT @rodtrent: Can ChatGPT work with your enter...</td>
      <td>[rt, @rodtrent, chatgpt, work, enterprise, dat...</td>
    </tr>
    <tr>
      <th>2998</th>
      <td>RT @rowancheung: 2. Boston Dynamics puts ChatG...</td>
      <td>[rt, @rowancheung, 2, boston, dynamic, put, ch...</td>
    </tr>
    <tr>
      <th>2999</th>
      <td>RT @Naho_May: J’ai demandé à ChatGPT des conse...</td>
      <td>[rt, @nahomay, asked, chatgpt, advice, fishing...</td>
    </tr>
  </tbody>
</table>
<p>3000 rows × 2 columns</p>
</div>


### Análisis de sentimiento

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>clean_tweet</th>
      <th>polarity</th>
      <th>subjectivity</th>
      <th>language</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>[rt, @gdb, chatgpt, tool, congress]</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>en</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[rt, @gdb, chatgpt, tool, congress]</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>en</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[rt, @moemicky18, chatgpt, failed, accounting,...</td>
      <td>-0.35000</td>
      <td>0.350000</td>
      <td>en</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[rt, @jeanprofitbiz, people, making, thousand,...</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>fr</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[chatgpt, mean, wet, lab, biologist, frankenst...</td>
      <td>-0.20625</td>
      <td>0.543750</td>
      <td>en</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[rt, @arabtribunenews, dr, firas, alharbi, wri...</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>ar</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[actually, redo, one, twice, chatgpt, kept, gi...</td>
      <td>0.00000</td>
      <td>0.100000</td>
      <td>en</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[rt, @rodtrent, chatgpt, work, enterprise, dat...</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>en</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[rt, @rowancheung, 2, boston, dynamic, put, ch...</td>
      <td>0.00000</td>
      <td>0.166667</td>
      <td>en</td>
    </tr>
    <tr>
      <th>0</th>
      <td>[rt, @nahomay, asked, chatgpt, advice, fishing...</td>
      <td>0.45000</td>
      <td>0.761111</td>
      <td>fr</td>
    </tr>
  </tbody>
</table>
<p>3000 rows × 4 columns</p>
</div>
    
## Polaridad
![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Polaridad.png)
    
Se observa una distribución relativamente normal, la mayor cantidad de tweets tiene una polaridad neutra cercana a cero. Se aprecia  que existen una mayor cantidad de tweets con una opinión positiva.

Sin embargo, es posible detectar una alta cantidad de comentarios muy negativos, esto puede deberse a una opinión muy ambivalente derivada del dilema moral ocasionado por las aplicaciones utilizadas para esta aplicación ChatGPT.


## Subjetividad
![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Subjetividad.png)
    
En el caso de la subjetividad, la distribución se observa relativamente plana, aunque tomando en cuenta que la escala de la frecuencia no es lineal, la cantidad de tweets con muy poca subjetividad (0 - 0.10) es alta, prácticamente una tercera parte de los tweets.

Es importante mencionar que, a pesar de lo anterior, sí existe un alto porcentaje de personas que tienen opiniones personales al respecto de este chatbot, posiblemente más las que tienen polaridad negativa. 


## Gráfico de dispersión entre polaridad y subjetividad 
![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Polaridad%20vs%20Subjetividad.png)
    
El diagrama de dispersión de ambas variables muestra cierta correlacion: a mayor subjetividad, los comentarios tienden a una mayor polaridad, mientras que opiniones más 'objetivas' mantienen una polaridad cercana a cero. 

Por tanto, parece que, si bien hay una discrepancia en opiniones, no existe un sesgo diferencial sobre la opinión analizada, pero sí se aprecia una mayor cantidad de opiniones en el sector positivo.

Claramente la opinión general tiene una perspectiva clara y neutra sobre esta aplicación, o contiene sólo noticias al respecto. Pero sí es posible apreciar opinión dividida y muy polarizada del tema, como ya se comentó previamente.

## Distribución de los idiomas

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>language</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>en</td>
      <td>1804</td>
    </tr>
    <tr>
      <th>1</th>
      <td>es</td>
      <td>409</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ja</td>
      <td>261</td>
    </tr>
    <tr>
      <th>3</th>
      <td>fr</td>
      <td>130</td>
    </tr>
    <tr>
      <th>4</th>
      <td>pt</td>
      <td>55</td>
    </tr>
    <tr>
      <th>5</th>
      <td>tr</td>
      <td>55</td>
    </tr>
    <tr>
      <th>6</th>
      <td>zh-cn</td>
      <td>48</td>
    </tr>
    <tr>
      <th>7</th>
      <td>vi</td>
      <td>35</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ar</td>
      <td>28</td>
    </tr>
    <tr>
      <th>9</th>
      <td>sq</td>
      <td>23</td>
    </tr>
  </tbody>
</table>
</div>



Principales idiomas:
1. Inglés: 1804
2. Español: 409
3. Japonés: 261
4. Francés: 130
5. Portugués: 55
6. Turco: 55
7. Chino: 48
8. Vietnamita: 35
9. Árabe: 28
10. Albanés: 23

![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Language.png)

Lo anterior muestra una gran participación por los países habla inglesa, casi en un 60%, lo que denota un mayor conocimiento e implicaciones para estos países, pero también existen muchos países de habla hispana y principalmente Japón que contribuyen con opiniones.


### Nube de palabras
    
![](https://github.com/AlbertoMCD/ChatGPT_tweets/blob/main/results/Nube%20de%20palabras.png)
    
En este wordcloud, se muestran las palabras más utilizadas como resultado final de nuestro análisis. Además de Chatgpt, otras palabras que se destacan entre los tweets son: AI, PROMPT, COURSE y OPENAI.

Estas palabras denotan principalmente un contexto neutro de opinión, pero también se aprecian las palabras REGULATORY,  THRILLED, PROBLEM, que pueden conllevar opiniones negativas al respecto.

## Conclusiones

La opinión pública en Twitter sobre el ChatBot ChatGPT tiene gran ambivalencia, pero principalmente se desembocan opiniones de polaridad positiva y gran cantidad de opiniones con poca subjetividad, lo que se interpreta como una herramienta que tiene futuro para aplicaciones provechosas y como un adelanto en tecnología deseable.

### Fuentes:

- [Cómo detectar y traducir múltiples idiomas para un proyecto de PLN (NLP)](https://www.ibidem-translations.com/edu/traduccion-idiomas-nlp/#:~:text=La%20función%20“detectar”%20y%20“traducir”%20de%20Python&text=Luego%20detecta%20el%20idioma%20del,proporcionado%20al%20idioma%20de%20destino.)
- [Deep Translator](https://pypi.org/project/deep-translator/)
- [Material del curso Desarrollo de Proyectos II](https://github.com/vcuspinera/UDG_MCD_Project_Dev_II)
- [Actividad 11: Estructura de repositorio](https://github.com/vcuspinera/UDG_MCD_Project_Dev_II/blob/main/actividades/11_Repo_structure.md)
- [Actividad 12: Visualización con Altair](https://github.com/vcuspinera/UDG_MCD_Project_Dev_II/blob/main/actividades/12_Viz_Altair.ipynb)
- [Actividad 13: Análisis Exploratorio de Datos (EDA)](https://github.com/vcuspinera/UDG_MCD_Project_Dev_II/blob/main/actividades/13_EDA.ipynb)
- [Actividad 18: Herramientas de texto](https://github.com/vcuspinera/UDG_MCD_Project_Dev_II/blob/main/actividades/18_Text_tools.ipynb)
- [Actividad 19: Análisis de texto](https://github.com/vcuspinera/UDG_MCD_Project_Dev_II/blob/main/actividades/19_Text_analysis.ipynb)
