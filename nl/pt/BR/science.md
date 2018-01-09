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

# A ciência por trás do serviço

O serviço do {{site.data.keyword.toneanalyzerfull}} baseia-se na teoria de psicolinguística, um campo de pesquisa que explora a relação entre o comportamento linguístico e as teorias psicológicas. O serviço usa a análise linguística e a correlação entre os recursos linguísticos de texto por escrito e tons emocionais e de linguagem para desenvolver pontuações para cada uma dessas dimensões de tom.
{: shortdesc}

Os pesquisadores de psicolinguística têm trabalhado para entender se as palavras que usamos em nossas vidas diárias refletem quem somos, como nos sentimos e como pensamos. Após várias décadas de pesquisa nessa área, agora é aceito na psicologia, em marketing e em outros campos que a linguagem reflete mais do que apenas o que desejamos dizer. A frequência com a qual usamos determinados tipos de palavras pode fornecer pistas sobre personalidade, estilo de pensamento, conexões sociais e estados emocionais.

Por exemplo, as pessoas apresentam vários tons em suas comunicações diárias: alegre ou triste, aberto ou conservador, analítico ou informal ([Gou et al., 2014](/docs/services/tone-analyzer/references.html#bib-gou), e [Jian et al., 2014](/docs/services/tone-analyzer/references.html#bib-jian)). Esses tons podem afetar a percepção da identidade on-line de uma pessoa e a efetividade de suas comunicações em diferentes contextos.

Além disso, em comunicações por e-mail de negócios, as pessoas mais provavelmente perceberão emoções negativas com maior intensidade do que emoções positivas ([Byron, 2008](/docs/services/tone-analyzer/references.html#bib-byron)). E em mídia social, as pessoas apresentam diferentes identidades on-line que afetam a impressão que os outros têm delas ([DiMicco e Millen, 2007](/docs/services/tone-analyzer/references.html#bib-dimicco)).

Muitas pessoas naturalmente leem uma mensagem e julgam os tons transmitidos pelo remetente. Mas um computador pode detectar os sinais divulgados por uma mensagem com precisão e automaticamente? Essa é uma das muitas perguntas desafiadoras para as quais os pesquisadores nos campos de inteligência artificial e de ciências cognitivas estão buscando respostas. Primeiro, com o serviço do {{site.data.keyword.personalityinsightsshort}} e, agora, com o serviço do {{site.data.keyword.toneanalyzershort}}, a IBM está começando a responder essa pergunta.

## Visão geral de pesquisa relacionada

Pesquisas mostraram uma correlação forte e estatisticamente significativa entre escolha de palavras e personalidade, emoções, atitudes, necessidades intrínsecas, valore e processos de pensamento. Muitos pesquisadores descobriram que as pessoas variam na frequência de uso de determinadas categorias de palavras ao escrever para blogs, ensaios e tweets e que esses meios de comunicação podem ajudar a prever diferentes aspectos da personalidade:

-   [Fast e Funder (2008)](/docs/services/tone-analyzer/references.html#bib-fast)
-   [Gill et al. (2009)](/docs/services/tone-analyzer/references.html#bib-gill)
-   [Golbeck et al. (2011)](/docs/services/tone-analyzer/references.html#bib-golbeck)
-   [Hirsh e Peterson (2009)](/docs/services/tone-analyzer/references.html#bib-hirsh)
-   [Yarkoni (2010)](/docs/services/tone-analyzer/references.html#bib-yarkoni)

A maioria desses trabalhos anteriores é baseada na descoberta de categorias de palavras psicologicamente significativas do uso de palavras na composição. Esta pesquisa serve como base para o trabalho da IBM no serviço do {{site.data.keyword.toneanalyzershort}}. Confiando nas descobertas científicas de pesquisa psicolinguística, a IBM está trabalhando para inferir características de personalidade das pessoas, seus estilos de pensamento e composição, suas emoções e suas necessidades e valores intrínsecos com base nas palavras que escrevem. A IBM usa seus modelos de aprendizado de máquina para avaliar essas características avaliando vários recursos da composição de uma pessoa.

## O modelo de propósito geral
{: #analysis}

O terminal de propósito geral analisa no conteúdo por escrito um conjunto de tons que são aplicáveis a uma ampla gama de usos. O serviço do {{site.data.keyword.toneanalyzershort}} calcula um scorecard que inclui os tons a seguir:

-   **Tom emocional** é derivado do trabalho da IBM na análise de emoção, que é uma estrutura conjunta que infere as emoções de um texto específico. Para derivar pontuações de emoção do texto, a IBM usa uma estrutura conjunta baseada em generalização empilhada; a generalização empilhada usa um modelo de alto nível para combinar modelos de nível inferior para obter maior precisão preditiva. Recursos, como n-gramas (unigramas, bigramas e trigramas), pontuação, emoticons, xingamentos, saudações (como "olá", "oi" e "obrigado") e polaridade do sentimento, são alimentados em algoritmos de aprendizado de máquina para classificar categorias de emoção.
-   **Tom da linguagem** é calculado da análise linguística com base em recursos aprendidos.

### Medindo a qualidade do serviço

A IBM mediu a qualidade do serviço do {{site.data.keyword.toneanalyzershort}} ao longo das dimensões do tom mencionado na seção anterior:

-   Categorias de *Tom emocional* foram avaliadas contra conjuntos de dados de emoção padrão, como ISEAR e SEMEVAL. Os resultados mostram que o desempenho médio do modelo conjunto (a pontuação macromédia F1 é cerca de 41% e 68%, respectivamente, para os dois conjuntos de dados) é estatisticamente melhor do que a melhor precisão relatada dos modelos de última geração (cujas pontuações macromédias F1 são cerca de 37% e 63%, respectivamente).
-   *Tom de linguagem* foi avaliado com um estudo aprofundado de mais de duzentas mil sentenças coletadas de fontes como fóruns de debates, discursos e mídia social. Dessas sentenças, a IBM selecionou aleatoriamente 1330 sentenças para tom analítico e 1000 sentenças para tom confiante e 1000 para tom hesitante. A IBM então enviou essas sentenças para o serviço do {{site.data.keyword.toneanalyzershort}} e também pediu que seres humanos as analisassem.

    Para a análise humana, a IBM usou uma plataforma de crowdsourcing chamada [CrowdFlower ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.crowdflower.com/){: new_window} para anotar as sentenças selecionadas com diferentes rótulos. Somente classificadores com índices de aprovação acima de 85% foram autorizados a participar das tarefas de anotação. Cinco anotadores rotularam cada sentença e a IBM usou o mais predominante dos cinco resultados anotados para determinar os rótulos finais.
    -   Para *tom analítico*, os seres humanos rotularam 915 das 1330 sentenças como analíticas, 411 como não analíticas e 4 como não compreensíveis. Ao comparar o rótulo previsto com esses rótulos de verdade absoluta, a IBM descobriu que a detecção de tom analítico recebeu uma pontuação F1 de 0,7518.
    -   Para *tom hesitante*, os seres humanos rotularam 292 das 1000 sentenças como hesitantes, 706 como não hesitantes e 2 como não compreensíveis. Ao comparar o rótulo previsto com os rótulos de verdade absoluta, a IBM descobriu que sua detecção do tento hesitante recebeu uma pontuação F1 de 0,6369.
    -   Para *tom confiante*, os seres humanos rotularam 623 das 1000 sentenças como confiantes, 374 como não confiantes e 3 como não compreensíveis. Ao comparar o rótulo previsto com os rótulos de verdade absoluta, a IBM descobriu que sua detecção de tom confiante recebeu uma pontuação F1 de 0,7288.

No geral, as diferenças entre os rótulos previstos e de verdade absoluta não são estatisticamente significativas. Isso indica que o serviço tem um bom desempenho.

## O modelo de engajamento do cliente

O terminal de engajamento do cliente identifica tons do domínio de atendimento ao cliente. Para selecionar os tons para avaliar com o modelo de engajamento do cliente, a IBM realizou primeiramente um estudo para identificar quais dimensões de tom são percebidas como importantes no domínio:

1.  A IBM selecionou um conjunto de 53 tons das dimensões de tons usadas em marketing, as dimensões usadas para descrever estilos de composição e as escalas de emoções e personalidades da psicologia.
1.  A IBM pediu aos trabalhadores no CrowdFlower para classificar a extensão com que os 53 atributos de tom descrevem uma elocução específica em 1000 conversas de atendimento ao cliente. Para simplificar a tarefa de classificação no contexto de crowdsourcing, a IBM dividiu os 53 tons em quatro subconjuntos. Os anotadores humanos precisavam apenas classificar um subconjunto dos tons; a IBM determinou então classificações para todos os tons com base em agregações desses resultados.
1.  A IBM executou a análise fatorial em uma matriz de correlações de 53 por 53 e localizou pelo menos sete fatores significativos (dimensões). A IBM determinou os nomes dos fatores para representar os conceitos mais importantes refletidos por cada uma das dimensões.

Essas etapas identificaram sete dimensões de tom importantes para o domínio de atendimento ao cliente: frustração, satisfação, animação, gentileza, indelicadeza, tristeza e compreensão.

### Coleta de dados

A IBM usou fóruns de suporte ao cliente no Twitter como a origem de dados de conversas para sua análise de tom no domínio de atendimento ao cliente. Muitas empresas usam o Twitter como um canal para fornecer suporte para seus clientes. Agentes são contratados e treinados para monitorar tweets que mencionam a empresa, para direcionar solicitações de ajuda e para fornecer suporte rápido para atender às necessidades dos clientes.

Para coletar o máximo de conversas possível, a IBM selecionou 62 marcas com contas de atendimento ao cliente dedicadas no Twitter. A IBM escolheu essas marcas para cobrir uma grande variedade de indústrias, localizações geográficas e escalas organizacionais. Em geral, a IBM coletou 2,6 milhões de solicitações de usuários entre 1 de junho e 1 de agosto de 2016.

### Anotação de dados

A IBM peneirou o conjunto de dados coletados para reter apenas aquelas conversas que receberam pelo menos uma resposta e que envolveram apenas um cliente e um agente. A IBM também removeu do conjunto de dados todas as conversas não em inglês e conversas que continham solicitações ou respostas com imagens. Para preservar a privacidade dos usuários e das empresas, a IBM substituiu todos os *@mentions* em cada conversa por *@customer*, *@[industry]_company* (por exemplo, *@ecommerce_company* ou *@telecommunication_company*), *@competitor_company* ou *@other_users*.

Esse processo de seleção identificou aproximadamente 96 mil elocuções de conversação para serem anotadas por trabalhadores do CrowdFlower. Para promover um maior entendimento do contexto de anotação, a IBM pediu aos trabalhadores que anotassem no nível da conversa, rotulando todas as elocuções envolvidas em uma conversa. Como a natureza subjetiva de alguns tons propostos poderia levar a percepções inconsistentes, a IBM pediu aos anotadores para indicarem o nível que sentiam que as elocuções demonstravam os tons em uma escala Likert de quatro pontos variando entre "Muito fortemente" e "De forma alguma". Uma escala Likert é preferível a uma escala binária simples de sim/não, pois acomoda uma maior tolerância para diferentes percepções e gera rótulos menos esparsos.

Cinco diferentes anotadores rotularam cada conversa. IBM usou apenas anotadores baseados nos EUA com um nível aceitável de desempenho em tarefas de anotação anteriores. A IBM também exigiu que os anotadores respondessem cinco perguntas de treinamento corretamente antes que pudessem continuar com as tarefas de anotação reais. As perguntas de treinamento asseguraram que os anotadores tinham um senso do que cada tom significa no contexto de atendimento ao cliente. A IBM também integrou perguntas de validação nas tarefas reais para validar ainda mais a qualidade dos rótulos dos anotadores.

A IBM usou a média de pontuação dos cinco anotadores como o rótulo final para cada elocução. A IBM então usou uma pontuação igual a 1 como o limite para converter os rótulos para valores binários. A IBM escolheu 1 como o limite com base em observações das distribuições de rótulos e no desempenho dos modelos com limites diferentes. Os resultados finais produziram a distribuição a seguir de elocuções: 9536 frustrados, 10.806 satisfeitos, 6107 animados, 63.853 gentis, 1688 indelicados, 24.954 tristes e 10.475 compreensivos.

### Modelos de tom de aprendizado

Com base nessas conversas de engajamento do cliente, a IBM treinou um modelo de aprendizado de máquina com base em Support Vector Machine (SVM) para prever o tom de novas elocuções de atendimento ao cliente. Para o modelo de aprendizado de máquina, a IBM utilizou várias categorias de recursos, incluindo recursos n-grama, recursos léxicos de vários dicionários, a existência de referências em segunda pessoa na conversa, alguns recursos específicos do diálogo, como agradecer ou pedir desculpas, e vários recursos de nível superior, como a existência de pontos de interrogação ou de exclamação consecutivos. 

A IBM constatou que cerca de 30% das amostras tinha mais de um tom associado. A IBM, portanto, optou por solucionar uma tarefa de classificação com vários rótulos em vez de uma tarefa de classificação com várias classes. Para cada tom, a IBM treinou o modelo de forma independente usando um paradigma One-vs-Rest (OVR). O paradigma usou as elocuções para cada classe como amostras positivas e todas as outras elocuções como amostras negativas. A IBM identificou os tons previstos com probabilidade de pelo menos 0,5 como os tons finais. Para vários tons, os dados de treinamento estavam muito desequilibrados; portanto, a IBM identificou o valor do peso ideal da função de custos para cada tom durante o treinamento.

A IBM usou precisão, recall e pontuação F para avaliar a precisão de seu modelo de classificação. O modelo demostrou alta precisão quando comparado a um conjunto de dados de referência.
