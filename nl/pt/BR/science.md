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

# A ciência por trás do serviço
{: #ssbts}

O serviço do {{site.data.keyword.toneanalyzerfull}} baseia-se na teoria de psicolinguística, um campo de pesquisa que explora a relação entre o comportamento linguístico e as teorias psicológicas. O serviço usa a análise linguística e a correlação entre os recursos linguísticos de texto por escrito e tons emocionais e de linguagem para desenvolver pontuações para cada uma dessas dimensões de tom.
{: shortdesc}

Pesquisadores de psicolinguística trabalham para entender se as palavras que as pessoas usam
no dia a dia refletem quem elas são, como se sentem e como pensam. Após várias décadas de pesquisa,
agora é aceito na psicologia, no marketing e em outros campos que a linguagem reflete mais do que o
que as pessoas querem dizer. A frequência com que as pessoas usam determinados tipos de palavras pode
fornecer pistas para sua personalidade, estilo de pensamento, conexões sociais e estados emocionais.

Por exemplo, as pessoas exibem vários tons em suas comunicações diárias: alegre ou triste, aberto
ou conservador, analítico ou informal
([Gou e outros, 2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gou) e [Jian e outros, 2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-jian)). Esses tons podem afetar a percepção da identidade on-line de uma pessoa e a efetividade de suas comunicações em diferentes contextos.

Além disso, em comunicações por e-mail de negócios, as pessoas mais provavelmente perceberão emoções negativas com maior intensidade do que emoções positivas ([Byron, 2008](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-byron)). E
nas mídias sociais, as pessoas apresentam diferentes identidades on-line que causam impacto na impressão
que os outros têm delas ([DiMicco e Millen, 2007](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-dimicco)).

Muitas pessoas leem naturalmente uma mensagem e julgam os tons que são transmitidos pelo remetente. Mas,
um computador consegue detectar os tons que são revelados por uma mensagem com precisão e automaticamente? Essa
é uma das muitas questões desafiadoras para as quais os pesquisadores nos campos de inteligência artificial e ciências cognitivas estão buscando respostas. Primeiro com o serviço {{site.data.keyword.personalityinsightsshort}} e agora com o serviço {{site.data.keyword.toneanalyzershort}}, a IBM está respondendo a essa questão.

## Visão geral de pesquisa relacionada
{: #sorr}

A pesquisa mostra uma correlação forte e estatisticamente significativa entre escolha de palavra
e a personalidade, as emoções, as atitudes, as necessidades intrínsecas, os valores e os processos de
pensamento. Vários pesquisadores descobriram que as pessoas variam em quantas vezes usam determinadas categorias de palavras quando escrevem em blogs, dissertações e tweets. Os pesquisadores descobriram
que essas mídias de comunicação podem ajudar a prever diferentes aspectos de personalidade:

-   [Fast e Funder (2008)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-fast)
-   [Gill e outros (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gill)
-   [Golbeck e outros (2011)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-golbeck)
-   [Hirsh e Peterson (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-hirsh)
-   [Yarkoni (2010)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-yarkoni)

A maioria desses trabalhos anteriores é baseada na descoberta de categorias de palavras psicologicamente significativas do uso de palavras na composição. Esta pesquisa serve como base para o trabalho da IBM no serviço do {{site.data.keyword.toneanalyzershort}}. Confiando nas descobertas científicas de pesquisa psicolinguística, a IBM está trabalhando para inferir características de personalidade das pessoas, seus estilos de pensamento e composição, suas emoções e suas necessidades e valores intrínsecos com base nas palavras que escrevem. A IBM usa seus modelos de aprendizado de máquina para avaliar essas características avaliando vários recursos da composição de uma pessoa.

## O modelo de propósito geral
{: #analysis}

O terminal de uso geral analisa o conteúdo escrito para um conjunto de tons que é aplicável
a uma ampla faixa de usos. O serviço do {{site.data.keyword.toneanalyzershort}} calcula um scorecard que inclui os tons a seguir:

-   O **tom emocional** é derivado do trabalho da IBM sobre análise de
emoções, que é uma estrutura de combinação que pressupõe as emoções de um texto. Para derivar pontuações
de emoção do texto, a IBM usa uma estrutura de combinação baseada em generalização empilhada; a
generalização empilhada usa um modelo de alto nível para combinar modelos de nível inferior para
alcançar maior precisão preditiva. Recursos, como n-gramas (unigramas, bigramas e trigramas), pontuação, emoticons, xingamentos, saudações (como "olá", "oi" e "obrigado") e polaridade do sentimento, são alimentados em algoritmos de aprendizado de máquina para classificar categorias de emoção.
-   **Tom da linguagem** é calculado da análise linguística com base em recursos aprendidos.

### Medindo a qualidade do serviço
{: #smqs}

A IBM mediu a qualidade do serviço {{site.data.keyword.toneanalyzershort}} ao longo
das dimensões de tom da seção anterior:

-   Categorias de *Tom emocional* foram avaliadas contra conjuntos de dados de emoção padrão, como ISEAR e SEMEVAL. Os resultados mostram que o desempenho médio do modelo de combinação (a pontuação
F1 da medida macro-average é em torno de 41% e 68% para os dois conjuntos de dados) é estatisticamente
melhor do que a melhor precisão relatada dos modelos de ponta (as pontuações F1 da medida macro-average ficam em
torno de 37% e 63%).
-   O *tom de linguagem* foi avaliado com um estudo aprofundado de mais de duzentas
mil sentenças que foram coletadas de fontes como fóruns de debate, discursos e mídia social. A IBM
selecionou aleatoriamente 1.330 das sentenças para tom analítico e 1.000 sentenças para cada um dos
tons confiante e hesitante. A IBM então enviou as sentenças para o serviço {{site.data.keyword.toneanalyzershort}} e também solicitou análise humana.

    Para a análise humana, a IBM usou uma plataforma de crowdsourcing denominada [CrowdFlower ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.crowdflower.com/){: new_window} para anotar as sentenças selecionadas com diferentes rótulos. Somente classificadores com índices de aprovação acima de 85% foram autorizados a participar das tarefas de anotação. Cinco anotadores rotularam cada sentença e a IBM usou o mais predominante dos cinco resultados anotados para determinar os rótulos finais.
    -   Para *tom analítico*, os seres humanos rotularam 915 das 1330 sentenças como analíticas, 411 como não analíticas e 4 como não compreensíveis. Ao comparar o rótulo previsto com esses rótulos de verdade absoluta, a IBM descobriu que a detecção de tom analítico recebeu uma pontuação F1 de 0,7518.
    -   Para *tom hesitante*, os seres humanos rotularam 292 das 1000 sentenças como hesitantes, 706 como não hesitantes e 2 como não compreensíveis. Ao comparar o rótulo previsto com os rótulos de verdade absoluta, a IBM descobriu que sua detecção do tento hesitante recebeu uma pontuação F1 de 0,6369.
    -   Para *tom confiante*, os seres humanos rotularam 623 das 1000 sentenças como confiantes, 374 como não confiantes e 3 como não compreensíveis. Ao comparar o rótulo previsto com os rótulos de verdade absoluta, a IBM descobriu que sua detecção de tom confiante recebeu uma pontuação F1 de 0,7288.

No geral, as diferenças entre os rótulos preditos e os de verdade absoluta não são estatisticamente significativas. Esse resultado indica que o serviço tem um bom desempenho.

## O modelo de engajamento do cliente
{: #scem}

O terminal de engajamento do cliente identifica tons do domínio de atendimento ao cliente. Para selecionar os tons para avaliar com o modelo de engajamento do cliente, a IBM realizou primeiramente um estudo para identificar quais dimensões de tom são percebidas como importantes no domínio:

1.  A IBM selecionou um conjunto de 53 tons nas dimensões usadas no marketing, as dimensões que são usadas para descrever os estilos de escrita e as escalas de emoção e personalidade da psicologia.

1.  A IBM pediu aos trabalhadores no CrowdFlower para classificar a extensão com que os 53 atributos de tom descrevem uma elocução específica em 1000 conversas de atendimento ao cliente. Para simplificar a tarefa de classificação no contexto de crowdsourcing, a IBM dividiu os 53 tons em quatro subconjuntos. Os anotadores
humanos precisavam classificar somente um subconjunto dos tons. A IBM então determinou as classificações
para todos os tons de agregações desses resultados.
1.  A IBM executou a análise fatorial em uma matriz de correlações de 53 por 53 e localizou pelo menos sete fatores significativos (dimensões). A IBM determinou os nomes dos fatores para representar os conceitos
mais importantes que são refletidos por cada uma das dimensões.

Essas etapas identificaram sete dimensões de tom importantes para o domínio de atendimento ao cliente: frustração, satisfação, animação, gentileza, indelicadeza, tristeza e compreensão.

### Coleta de dados
{: #sdc}

A IBM usou fóruns de suporte ao cliente no Twitter como a origem de dados de conversas para sua análise de tom no domínio de atendimento ao cliente. Muitas empresas usam o Twitter como um canal para fornecer suporte para seus clientes. Agentes são contratados e treinados para monitorar tweets que mencionam a empresa, para direcionar solicitações de ajuda e para fornecer suporte rápido para atender às necessidades dos clientes.

Para coletar o máximo de conversas possível, a IBM selecionou 62 marcas com contas de atendimento ao cliente dedicadas no Twitter. A IBM escolheu essas marcas para cobrir uma grande variedade de indústrias, localizações geográficas e escalas organizacionais. Em geral, a IBM coletou 2,6 milhões de solicitações de usuários entre 1 de junho e 1 de agosto de 2016.

### Anotação de dados
{: #sda}

A IBM peneirou o conjunto de dados coletados para reter apenas aquelas conversas que receberam pelo menos uma resposta e que envolveram apenas um cliente e um agente. A IBM também removeu do conjunto de dados todas as conversas não em inglês e conversas que continham solicitações ou respostas com imagens. Para preservar a privacidade dos usuários e das empresas, a IBM substituiu todos os *@mentions* em cada conversa por *@customer*, *@[industry]_company* (por exemplo, *@ecommerce_company* ou *@telecommunication_company*), *@competitor_company* ou *@other_users*.

Esse processo de seleção identificou aproximadamente 96 mil elocuções de conversação para serem anotadas por trabalhadores do CrowdFlower. Para promover um maior entendimento do contexto de anotação, a IBM pediu aos trabalhadores que anotassem no nível da conversa, rotulando todas as elocuções envolvidas em uma conversa. A natureza subjetiva de alguns dos tons propostos pode levar a percepções inconsistentes. Então, a IBM solicitou aos anotadores que indicassem com qual intensidade eles sentiam que as elocuções demonstravam
os tons em uma escala Likert de quatro pontos que variava de "Totalmente" até "De forma alguma". Uma escala Likert é preferível a uma escala binária simples de sim/não, pois acomoda uma maior tolerância para diferentes percepções e gera rótulos menos esparsos.

Cinco diferentes anotadores rotularam cada conversa. IBM usou apenas anotadores baseados nos EUA com um nível aceitável de desempenho em tarefas de anotação anteriores. A IBM também exigiu que os anotadores respondessem cinco perguntas de treinamento corretamente antes que pudessem continuar com as tarefas de anotação reais. As perguntas de treinamento asseguraram que os anotadores tinham um senso do que cada tom significa no contexto de atendimento ao cliente. A IBM também integrou perguntas de validação nas tarefas reais para validar ainda mais a qualidade dos rótulos dos anotadores.

A IBM usou a média de pontuação dos cinco anotadores como o rótulo final para cada elocução. A IBM então usou uma pontuação igual a 1 como o limite para converter os rótulos para valores binários. A IBM escolheu 1 como o limite com base em observações das distribuições de rótulos e no desempenho dos modelos com limites diferentes. Os resultados finais produziram a distribuição a seguir de elocuções: 9536 frustrados, 10.806 satisfeitos, 6107 animados, 63.853 gentis, 1688 indelicados, 24.954 tristes e 10.475 compreensivos.

### Modelos de tom de aprendizado
{: #sltm}

Com base nessas conversas de engajamento do cliente, a IBM treinou um modelo de aprendizado de máquina com base em Support Vector Machine (SVM) para prever o tom de novas elocuções de atendimento ao cliente. Para
o modelo de aprendizado de máquina, a IBM alavancou várias categorias de recursos:

-   Recursos N-gram
-   Recursos léxicos de vários dicionários
-   A existência de referências de segunda pessoa na conversa
-   Algumas características específicas do diálogo, como dizer obrigado ou pedir desculpas
-   Vários recursos de nível superior, como a existência de pontos de interrogação ou pontos de exclamação consecutivos

A IBM constatou que cerca de 30% das amostras tinha mais de um tom associado. Portanto, a IBM optou
por resolver uma tarefa de classificação com vários rótulos em vez de uma tarefa de classificação com várias classes. Para cada tom, a IBM treinou o modelo de forma independente usando um paradigma One-vs-Rest (OVR). O paradigma usou as elocuções para cada classe como amostras positivas e todas as outras elocuções como amostras negativas. A IBM identificou
os tons que foram preditos com pelo menos 0,5 de probabilidade como os tons finais. Para vários tons, os dados de treinamento estavam muito desequilibrados; portanto, a IBM identificou o valor do peso ideal da função de custos para cada tom durante o treinamento.

A IBM usou precisão, recall e pontuação F para avaliar a precisão de seu modelo de classificação. O modelo demostrou alta precisão quando comparado a um conjunto de dados de referência.
