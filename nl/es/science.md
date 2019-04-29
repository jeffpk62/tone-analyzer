---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-07"

subcollection: tone-analyzer

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# La ciencia detrás del servicio
{: #ssbts}

El servicio {{site.data.keyword.toneanalyzerfull}} se basa en la teoría de la psicolingüística, un campo de investigación que explora la relación entre el comportamiento lingüístico y teorías psicológicas. El servicio utiliza el análisis lingüístico y la correlación entre las características lingüísticas del texto escrito y los tonos emocional y de lenguaje para desarrollar puntuaciones para cada una de estas dimensiones del tono.
{: shortdesc}

Los investigadores en el campo de la psicolingüística trabajan para comprender si las palabras que la gente utiliza en su vida cotidiana reflejan quiénes son, cómo se sienten y cómo piensan. Después de varias décadas de investigación, hoy en día, en psicología, marketing y en otros campos se acepta que el lenguaje refleja mucho más de la gente quiere decir. La frecuencia con la que las personas utilizan ciertos tipos de palabras puede proporcionar pistas sobre su personalidad, su estilo de pensamiento, sus conexiones sociales y sus estados emocionales.

Por ejemplo, las personas utilizan diferentes tonos en su comunicación diaria: alegre o triste, abierto o conservador, analítico o informal ([Gou et al., 2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gou), y [Jian et al., 2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-jian)). Estos tonos pueden afectar a la percepción de la identidad en línea de una persona y a la eficacia de su comunicación en diferentes contextos.

Además, en las comunicaciones por correo electrónico de una empresa, es probable que las personas perciban las emociones negativas con mayor intensidad que las emociones positivas ([Byron, 2008](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-byron)). Y, en las redes sociales, las personas presentan diferentes identidades en línea que afectan a la impresión que los demás tienen sobre ellos ([DiMicco y Millen, 2007](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-dimicco)).

Mucha gente lee un mensaje y juzga con naturalidad los tonos que expresa el remitente. Pero, ¿puede una máquina detectar los tonos que se desprenden de un mensaje de forma precisa y automática? Esta cuestión es uno de los temas clave a los que los investigadores en el campo de inteligencia artificial y ciencias cognitivas buscan respuesta. Primero con el servicio {{site.data.keyword.personalityinsightsshort}} y ahora con el servicio {{site.data.keyword.toneanalyzershort}}, IBM está respondiendo a esta pregunta.

## Visión general de investigaciones relacionadas
{: #sorr}

Las investigaciones demuestran una fuerte correlación estadísticamente significativa entre la selección de palabras y la personalidad, las emociones, las actitudes, las necesidades intrínsecas, los valores y los procesos del pensamiento. Varios investigadores han descubierto que varía la frecuencia con que las personas utilizan determinadas categorías de palabras cuando escriben en blogs, ensayos y tweets. Los investigadores han encontrado que estos medios de comunicación pueden ayudar a predecir diferentes aspectos de la personalidad:

-   [Fast y Funder (2008)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-fast)
-   [Gill et al. (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gill)
-   [Golbeck et al. (2011)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-golbeck)
-   [Hirsh y Peterson (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-hirsh)
-   [Yarkoni (2010)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-yarkoni)

La mayoría de estas obras previas se basan en la búsqueda de categorías de palabras psicológicamente significativas a partir del uso de las palabras en comunicaciones por escrito. Esta investigación sirve como base para la labor de IBM desarrollada en el servicio {{site.data.keyword.toneanalyzershort}}. Tomando como base los hallazgos científicos en cuanto a investigación psicolingüística, IBM sigue trabajando para detectar características de la personalidad de las personas, su estilo de pensamiento y de escritura, sus emociones y sus necesidades y valores intrínsecos a partir de las palabras que escriben. IBM utiliza sus modelos de aprendizaje de máquina para evaluar estas características, mediante la evaluación de diversos rasgos en la forma de escribir de una persona.

## El modelo de finalidad general
{: #analysis}

El punto final de finalidad general analiza el contenido escrito para descubrir un conjunto de tonos que se aplican a un amplio abanico de usos. El servicio {{site.data.keyword.toneanalyzershort}} calcula una puntuación que incluye los tonos siguientes:

-   El **tono emocional** se deriva del trabajo de IBM sobre el análisis de emociones, que es un marco conjunto que infiere emociones a partir de un texto. Para obtener puntuaciones de las emociones a partir de un texto, IBM utiliza un marco conjunto basado en una generalización; esta generalización utiliza un modelo general para combinar modelos individuales a fin de mejorar la precisión de las predicciones. Se introducen características como n-gramas (unigramas, bigramas y trigramas), puntuación, emoticonos, tacos, saludos (como "hola," "qué tal" y "gracias") y polaridad de sentimientos en algoritmos de aprendizaje de máquina para clasificar las categorías de las emociones.
-   El **tono del lenguaje** se calcula a partir de análisis lingüísticos basados en las características aprendidas.

### Evaluación de la calidad del servicio
{: #smqs}

IBM evalúa la calidad del servicio {{site.data.keyword.toneanalyzershort}} junto con las dimensiones de los tonos de la sección anterior.

-   Las categorías del *tono emocional* se comparan con conjuntos de datos estándares de emociones, como ISEAR y SEMEVAL. Los resultados muestran que el rendimiento medio del modelo conjunto (la puntuación macro media de F1 está alrededor del 41 y el 68 por ciento, para los dos conjuntos de datos) es estadísticamente mejor que la mejor precisión alcanzada por modelos avanzados (la puntuación macro media de F1 es de alrededor del 37 y el 63 por ciento).
-   El *tono del lenguaje* se ha evaluado con un estudio a fondo de más de doscientas mil frases recopiladas de fuentes tales como foros de debate, discursos y redes sociales. IBM ha seleccionado aleatoriamente 1330 frases para el tono analítico y 1000 frases para el tono confiado y 1000 más para el tono indeciso. A continuación, IBM envió las frases al servicio {{site.data.keyword.toneanalyzershort}} y también pidió a personas que las analizaran.

    Para el análisis humano, IBM ha utilizado una plataforma de varias fuentes denominada [CrowdFlower ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.crowdflower.com/){: new_window} para anotar las frases seleccionadas con distintas etiquetas. Solo se ha permitido participar en las tareas de anotación a los evaluadores con puntuaciones de aprobación superiores al 85 por ciento. Cinco anotadores han etiquetado cada frase e IBM ha utilizado los cinco resultados que más veces se han anotado para determinar las etiquetas finales.
    -   Para el *tono analítico*, los participantes han etiquetado 915 de las 1330 frases como analíticas, 411 como no analíticas y 4 como incomprensibles. Después de comparar las etiquetas previsibles con las etiquetas reales, IBM ha concluido que su detección de tono analítico ha recibido una puntuación de F1 de 0,7518.
    -   Para el *tono de indecisión*, los participantes han etiquetado 292 de las 1000 frases como de indecisión, 706 como no de indecisión y 2 como incomprensibles. Después de comparar las etiquetas previsibles con las etiquetas reales, IBM ha concluido que su detección de tono de indecisión ha recibido una puntuación de F1 de 0,6369.
    -   Para el *tono de confianza*, los participantes han etiquetado 623 de las 1000 frases como de confianza, 374 como no de confianza y 3 como incomprensibles. Después de comparar las etiquetas previsibles con las etiquetas reales, IBM ha concluido que su detección de tono de confianza ha recibido una puntuación de F1 de 0,7288.

En general, las diferencias entre las etiquetas previsibles y las reales no son estadísticamente significativas. Este resultado indica que el servicio funciona correctamente.

## El modelo de fidelización del cliente
{: #scem}

El punto final de fidelización del cliente identifica tonos del ámbito de la asistencia al cliente. Para seleccionar los tonos a fin de evaluarlos con el modelo de fidelización del cliente, IBM ha realizado un primer estudio para identificar las dimensiones de tono que se consideran importantes en este ámbito:

1.  IBM ha seleccionado un conjunto de 53 tonos de las dimensiones que se utilizan en marketing, las dimensiones que se utilizan para describir los estilos de escritura y las escalas de emociones y personalidad que se utilizan en psicología.
1.  IBM ha solicitado a los participantes en CrowdFlower que clasifiquen la medida en que los 53 atributos de un tono describen una determinada expresión en 1000 conversaciones relacionadas con la asistencia al cliente. Para simplificar la tarea de clasificación en el entorno de varias fuentes, IBM ha dividido los 53 tonos en cuatro subconjuntos. Los participantes solo tenían que clasificar un subconjunto de los tonos. Luego IBM ha determinado clasificaciones para todos los tonos, mediante la agregación de estos resultados.
1.  IBM ha realizado un análisis de factores en una matriz de correlaciones de 53 por 53 y ha detectado al menos siete factores (dimensiones) significativos. IBM ha elegido nombres de factores que representan los conceptos más importantes que refleja cada una de las dimensiones.

Se han identificado siete dimensiones de tono importantes para el ámbito de asistencia al cliente: frustración, satisfacción, entusiasmo, cortesía, descortesía, tristeza y empatía.

### Recopilación de datos
{: #sdc}

IBM ha utilizado foros de soporte al cliente de Twitter como fuente de datos de conversaciones para su análisis de tonos en el ámbito de la asistencia al cliente. Muchas empresas utilizan Twitter como canal para proporcionar soporte a sus clientes. Se contratan y se forman agentes para que supervisen los tweets en los que se menciona a la empresa, den respuesta a las solicitudes de ayuda y ofrezcan un soporte rápido que solucione los requisitos de los clientes.

Para recopilar el mayor número posible de conversaciones, IBM ha seleccionado 62 marcas con cuentas dedicadas al servicio al cliente en Twitter. IBM ha elegido marcas que cubran diversas industrias, ubicaciones geográficas y escalas en la organización. En total, IBM ha recopilado 2,6 millones de solicitudes de usuarios entre el 1 de junio y el 1 de agosto de 2016.

### Anotación de datos
{: #sda}

IBM ha filtrado los datos recopilados para quedarse solo con las conversaciones que han recibido al menos una respuesta y en las que solo han intervenido un cliente y un agente. IBM también ha eliminado de los datos las conversaciones que no se han mantenido en inglés y las que contenían solicitudes o respuestas con imágenes. Para preservar la privacidad de los usuarios y de las empresas, IBM ha sustituido todas las *@mentions* de cada conversación por *@customer*, *@[industry]_company* (por ejemplo, *@ecommerce_company* o *@telecommunication_company*), *@competitor_company* o *@other_users*.

En este proceso de selección se han identificado unas 96.000 expresiones de conversaciones que han anotado los participantes de CrowdFlower. Para facilitar la comprensión del contexto de la anotación, IBM ha pedido a los participantes que anotaran un nivel de conversación, etiquetando todas las expresiones que aparecían en una conversación. La naturaleza subjetiva de algunos de los tonos propuestos podría llevar a percepciones incoherentes. Por esto, IBM ha solicitado a los anotadores que indicaran el nivel con que pensaban que las expresiones mostraban los tonos, en una escala de Likert de cuatro niveles que iban de "mucho" a "en absoluto". Es preferible utilizar una escala de Likert que una simple escala binaria de tipo sí/no porque permite evaluar diversas percepciones y genera etiquetas menos dispersas.

Cinco anotadores han etiquetado cada conversación. IBM solo ha utilizado anotadores americanos con unos resultados aceptables en las tareas de anotación anteriores. IBM también ha solicitado a los anotadores que contestaran correctamente a cinco preguntas de formación para poder continuar con las tareas de anotación reales. Con estas preguntas de formación, IBM se aseguraba de que los anotadores comprendían perfectamente el significado de cada tono en el contexto del servicio al cliente. IBM también ha incorporado preguntas de validación de tareas reales para validar mejor la calidad de las etiquetas de los anotadores.

IBM ha utilizado un promedio de las clasificaciones de los cinco anotadores en la etiqueta final de cada expresión. Luego IBM ha utilizado una puntuación de 1 para convertir las etiquetas en valores binarios. IBM ha elegido 1 como umbral basándose en observaciones de las distribuciones de las etiquetas y en el resultado de los modelos con distintos umbrales. Los resultados finales han dado lugar a la siguiente distribución de expresiones: 9.536 de frustración, 10.806 de satisfacción, 6.107 de entusiasmo, 63.853 de cortesía, 1.688 de descortesía, 24.954 de tristeza y 10.475 de empatía.

### Modelos de tonos de aprendizaje
{: #sltm}

A partir de las conversaciones relacionadas con la fidelización del cliente, IBM ha formado un modelo de aprendizaje de máquina basado en SVM (Support Vector Machine) para pronosticar el tono de las nuevas expresiones de asistencia al cliente. Para el modelo de aprendizaje automático, IBM ha aprobado varias categorías de características:

-   Características de n-gram
-   Características léxicas de varios diccionarios
-   La existencia de referencias de segunda persona en la conversación
-   Algunas características específicas del diálogo como, por ejemplo, dar las gracias o disculparse
-   Varias características de nivel superior, como la existencia de marcas de interrogación consecutivas o marcas de exclamación

IBM ha concluido que alrededor del 30 por ciento de los ejemplos tenían más de un tono asociado. Por lo tanto, IBM ha optado por resolver una tarea de clasificación de varias etiquetas en lugar de una tarea de clasificación de varias clases. Para cada tono, IBM ha formado el modelo independiente utilizando un paradigma OVT (Oneo-vs-Rest). El paradigma ha utilizado las expresiones correspondientes a cada clase como ejemplos positivos y todas las demás expresiones como ejemplos negativos. IBM ha identificado los tonos que se pronosticaron con una probabilidad de al menos un 0,5 como tonos finales. Para varios tonos, los datos de formación estaban muy desequilibrados; IBM ha identificado el valor ponderado óptimo peso de la función de coste para cada tono durante la formación.

IBM ha utilizado funciones de precisión, recuperación y clasificación F para evaluar la precisión de su modelo de clasificación. El modelo ha mostrado un alto nivel de precisión en comparación con el conjunto de datos estándares de referencia.
