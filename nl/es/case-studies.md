---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

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

# Casos prácticos

Lea estos casos prácticos para inspirarse sobre lo que puede hacer con el servicio {{site.data.keyword.toneanalyzerfull}}. En los casos se describe la correlación entre los tonos mostrados y los resultados esperados. La correlación puede ser positiva o negativa y está comprendida entre -1.0 y 1.0.
{: shortdesc}

## Predicción del nivel de satisfacción del cliente en los foros de soporte

IBM ha analizado foros de soporte al cliente de una empresa de software centrada en diversas industrias. La compañía contribuye de forma activa en los foros de soporte al cliente. Los usuarios pueden asignar *Kudos* (elogios) a las respuestas que encuentran útiles. 

### Objetivos

Predecir el nivel de satisfacción del cliente a partir del tono de la pregunta y de la respuesta. IBM presupone que una respuesta con Kudos significa que el usuario está satisfecho.

### Acciones

-   Se han rastreado las 1000 entradas más recientes de varios foros, asegurándose de incluir el número de respuestas con o sin Kudos. 
-   Se han analizado tanto las preguntas como las respuestas. 
-   Se han aplicado avanzados clasificadores, como Bayes, Support Vector Machine (SVM) y algoritmos Random Forest, para predecir si una respuesta debería recibir Kudos. 

### Resultados

El servicio puede predecir los Kudos con una exactitud del 66 por ciento. IBM ha encontrado los siguientes correlaciones entre los tonos que devuelve una respuesta del foro y si la respuesta recibe Kudos: 

-   Cuanta más confianza se muestra en la respuesta, mayor es la probabilidad de que reciba Kudos (correlación de 0,23 entre una puntuación alta en confianza y Kudos).
-   Cuanta más indecisión se percibe en la respuesta, menor es la probabilidad de que reciba Kudos (correlación negativa de -0,27 entre una puntuación alta en indecisión y Kudos).

## Predicción del nivel de satisfacción del cliente en respuestas de Twitter

Muchas empresas están pasando su sistema de soporte al cliente a Twitter. Twitter permite ofrecer respuestas en tiempo real, lo que ayuda a que la marca se perciba como una empresa de gente real que se preocupa por sus clientes.

IBM ha analizado 333 conversaciones de soporte al cliente en Twitter. Los clientes estaban satisfechos con 240 de las conversaciones y no lo estaban con 93 de las interacciones. IBM ha medido el nivel de satisfacción después de leer las conversaciones y de etiquetarlas. Las respuestas se etiquetaban como "cliente satisfecho" cuando resolvían el problema y el cliente parecía satisfecho y como "cliente no satisfecho" cuando el problema no se solucionaba a gusto del cliente. 

### Objetivos

Validar si el tono de las conversaciones entre el agente y el cliente tiene efecto sobre el grado de satisfacción general del cliente. También identificar las características del tono que afectan de forma significativa al nivel de satisfacción del cliente. 

### Acciones

-   Se ha identificado puntuación, menciones y enlaces a partir de los tweets.
-   Se ha dividido cada interacción entre tweets del cliente y tweets del equipo de soporte.
-   Se ha analizado cada lado de la conversación con el servicio {{site.data.keyword.toneanalyzershort}} y se han comparado los resultados para encontrar correlaciones. 

### Resultados

El servicio puede predecir el nivel de satisfacción del cliente a partir del tono de la respuesta con una precisión del 67 por ciento. IBM ha descubierto la siguiente correlación entre el tono de los tweets del cliente y si el cliente estaba satisfecho con la respuesta: 

-   Cuanto más enfadado está el cliente, menor es la probabilidad de que quede satisfecho con la respuesta (correlación negativa de -0,198 entre una puntuación alta de ira en un tweet de un cliente y el grado de satisfacción del cliente).

## Predicción del aplauso de TED Talk

TED es una organización sin ánimo de lucro que realiza conferencias globales con el eslógan "Ideas worth spreading" (Ideas que vale la pena difundir). Los ponentes de TED Talk disponen de 18 minutos para contar historias innovadoras y cautivadoras sobre una amplia gama de temas relacionados con la investigación, la ciencia y la cultura. No todas las ponencias de TED Talks tienen éxito, y una forma de medir el grado de satisfacción de la audiencia ante una ponencia consiste en medir la cantidad de aplausos que recibe. 

### Objetivos

Descubrir los patrones de tono de TED Talks que generan aplausos y los que no. También predecir el nivel de aplausos en función del tono de una frase. 

### Acciones

Las frases que han recibido aplausos ya estaban etiquetadas en el conjunto de datos. 

-   Se han revisado 1931 TED Talks.
-   Se ha clasificado como "texto con aplauso" una frase etiquetada con "Aplauso". También se han etiquetado las tres frases anteriores y las tres frases posteriores a la frase con "texto con aplauso" como "texto sin aplauso".
-   Se ha analizado el texto con aplauso y sin aplauso dentro del servicio {{site.data.keyword.toneanalyzershort}}. 
-   En función de las correlaciones encontradas, se han creado clasificadores para predecir el aplauso en otros TED Talks basándose en su tono. 

### Resultados

El servicio puede predecir el aplauso con una exactitud del 75 por ciento. IBM ha encontrado las siguientes correlaciones entre el tono de cada una de las frases y si dichas frases han recibido aplausos: 

-   Cuanto mayor es la tristeza con la que se expresa un ponente, menor es la probabilidad de que reciba un aplauso (correlación negativa de -0,055 entre una puntuación alta en tristeza y aplauso). 
-   Cuanta menos emoción exprese o más impersonal parezca el ponente, menor es la probabilidad de que reciba aplausos (correlación negativa de -0,29 entre una puntuación alta en análisis y aplauso). 
-   Cuanto más contento y satisfecho parece el ponente, mayor es la probabilidad de que reciba aplausos (correlación de 0,21 entre un valor alto en alegría y aplauso). 

## Predicción de retweets y Me gusta de Twitter

El establecimiento de marca en Twitter se está convirtiendo en un requisito para que una empresa triunfe. Una parte esencial para establecerse a nivel personal o como empresa en Twitter es conseguir muchos Me gusta y retweets.

### Objetivos

Encontrar correlaciones entre el tono del tweet y si el tweet gusta y se retweetea.

### Acciones

-   Se han rastreado 5881 tweets de diversas cuentas de empresas en Twitter.
-   Se ha identificado puntuación, menciones y enlaces a partir de los tweets.
-   Se ha analizado cada tweet con el servicio {{site.data.keyword.toneanalyzershort}} y se han comparado los resultados para encontrar correlaciones. 

### Resultados

IBM ha encontrado correlaciones entre el tono de un tweet y si gusta, y entre el tono de un tweet y si se retweetea. 

## Predicción de emparejamientos en citas en línea

Millones de personas de todo el mundo utilizan servicios de citas en línea para encontrar su media naranja. La gente utiliza servicios de citas en línea para encontrar personas con las que tienen mucho en común y para venderse como posibles parejas. 

### Objetivos

Correlacionar el tono del perfil de una persona con el tono de perfil de un potencial emparejamiento. También descubrir si la correlación puede predecir correctamente emparejamientos. 

### Acciones

-   Se han rastreado unos 50.000 perfiles de usuario.
-   Se ha analizado cada perfil con el servicio {{site.data.keyword.toneanalyzershort}}. 
-   Se han definido potenciales emparejamientos como los que se comunican mediante el sitio.
-   Se ha comparado el análisis de tono de posibles emparejamientos para encontrar correlaciones.
-   Se ha desarrollado un modelo estadístico a partir de la similitud del tono de los perfiles para predecir si dos usuarios se van a comunicar. Luego se ha comparado el modelo con varias líneas que tienen en cuenta otros atributos, como la demografía.

### Resultados

La similitud del tono entre perfiles puede aportar una mejora del 45 por ciento en la predicción de si dos usuarios se van a comunicar, en comparación con los métodos de predicción que utilizan habitualmente los sitios web de citas. IBM ha descubierto una fuerte correlación entre la similitud del tono y el número de mensajes intercambiados, tal como se muestra en la imagen siguiente.

![Una fuerte correlación entre los tonos analizados y el número de mensajes intercambiados](images/case-study.png)
