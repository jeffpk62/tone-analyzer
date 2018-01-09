---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-28"

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

# Notas sobre a liberação

As seções a seguir documentam os novos recursos e mudanças que foram incluídos para cada liberação do serviço do {{site.data.keyword.toneanalyzershort}}. As mudanças não quebram o código existente.
{: shortdesc}

> **Nota:** as notas sobre a liberação agora documentam a *versão do serviço* e a *versão da interface* de cada atualização. Você especifica a *versão da interface* com o parâmetro de consulta `version` para usar os novos recursos e funcionalidades disponíveis com a atualização. O serviço retorna ambas as versões com o cabeçalho de resposta `X-Service-API-Version`.

## 28 de setembro de 2017
{: #September2017b}

**Versão do serviço:** `3.4.1`<br/> **Versão da interface:** `2017-09-21`

-   O limite de regulagem do número máximo de solicitações que um nome do usuário individual do {{site.data.keyword.Bluemix_notm}} pode enviar aumentou para 1200 solicitações por minuto. O serviço retornará o código de resposta HTTP 429 *Muitas solicitações* se um usuário exceder esse limite.

## 25 de setembro de 2017
{: #September2017a}

**Versão do serviço:** `3.4.1`<br/> **Versão da interface:** `2017-09-21`

-   O terminal de propósito geral (o método `/v3/tone`) mudou conforme a seguir:

    -   Suporta conteúdo de entrada em francês (`fr`) além do inglês.
    -   Não retorna mais tons sociais.
    -   Não retorna mais `disgust` com os tons de emoção.
    -   Omite qualquer tom cuja pontuação seja menor que `0,5`. Essa qualificação corresponde à resposta do método `/v3/tone_chat`.
    - Já não retorna categorias de tom (o campo `tone_categories`) como parte da saída. Todos os tons cujos valores cumprem o limite de qualificação são retornados como parte de um único objeto `tones`. Como antes, os tons são sempre retornados para o documento completo e para cada sentença individual por padrão.
    - Não mais aceita um parâmetro de consulta `tones` para limitar a saída para tons especificados. Todos os tons de qualificação são retornados para cada solicitação. Incluir o parâmetro com uma solicitação não causa um erro, mas não tem nenhum efeito na resposta.
    - Não mais retorna os campos `input_from` e `input_to` para sentenças individuais. Além dos resultados de sua análise, o método agora retorna apenas um ID e o texto de cada sentença.

-   O serviço agora retorna o código de resposta HTTP 200 em vez de 400 para uma entrada parcialmente correta nos casos a seguir:

    -   Para o método `/v3/tone`, se você enviar mais de 128 KB ou 1000 sentenças de conteúdo de entrada, o serviço retornará um campo `warning` como parte de sua resposta. O serviço analisa as primeiras 1000 sentenças para análise no nível do documento e, como faz atualmente, apenas as primeiras 100 sentenças para análise no nível da sentença. Versões anteriores do serviço retornavam o código de resposta 400 para a solicitação se você excedesse qualquer um dos dois limites. Observe também que o serviço agora analisa sentenças que têm menos de três palavras.
    -   Para o método `/v3/tone_chat`, se você enviar mais de 50 elocuções, o serviço retornará um campo `warning` para o conteúdo geral b= no nível de `utterances_tone` da resposta; ele analisa apenas as primeiras 50 elocuções. Se você enviar uma única elocução com mais de 500 caracteres, o serviço retornará um campo `error` para essa elocução e não a analisará. Versões anteriores do serviço retornavam o código de resposta 400 se você excedesse qualquer um dos dois limites. Observe que se todas as elocuções da entrada tiverem mais de 500 caracteres, o serviço ainda assim retornará o código de resposta 400 para a solicitação.

-   O serviço agora regula o número de solicitações que aceita de um único usuário. O serviço retornará o código de resposta HTTP 429 *Muitas solicitações* se receber mais de 600 solicitações por minuto de um nome do usuário individual do {{site.data.keyword.Bluemix_notm}}.

-   As mudanças a seguir se aplicam aos terminais de propósito geral e de engajamento do cliente:

    -   A versão da interface especificada com o parâmetro `version` é `2017-09-21` para usar a versão mais recente do serviço.
    -   A documentação foi atualizada para observar que o serviço pode produzir saída localizada em vários idiomas. Use o cabeçalho da solicitação `Accept-Language` para especificar o idioma desejado.

## 6 de julho de 2017
{: #July2017b}

**Versão do serviço:** `3.3.6`<br/> **Versão da interface:** `2016-05-19`

O serviço foi atualizado para a correção de um pequeno defeito no terminal de engajamento do cliente.

## Liberações mais antigas

-   [1 de julho de 2017](#July2017a)
-   [8 de maio de 2017](#May2017)
-   [17 de abril de 2017](#April2017)
-   [15 de março de 2017](#March2017)
-   [1 de dezembro de 2016](#December2016)
-   [18 de outubro de 2016](#October2016b)
-   [3 de outubro de 2016](#October2016a)
-   [19 de maio de 2016](#May2016)

### 1 de julho de 2017
{: #July2017a}

**Versão do serviço:** `3.3.5`<br/> **Versão da interface:** `2016-05-19`

O terminal de engajamento do cliente do serviço do {{site.data.keyword.toneanalyzershort}} agora está generally available (GA). Todas as chamadas ao terminal agora são cobradas pela mesma taxa que as chamadas para o terminal de propósito geral.

### 8 de maio de 2017
{: #May2017}

**Versão do serviço:** `3.3.4`<br/> **Versão da interface:** `2016-05-19`

A IBM atualizou os modelos de pontuação do tom de emoção e do tom de engajamento de atendimento ao cliente expandindo ainda mais o conjunto de dados de treinamento. Os modelos agora têm maior precisão no conjunto de dados da referência.

### 17 de abril de 2017
{: #April2017}

-   Um novo conjunto de tons específico do domínio de engajamento do cliente agora está disponível: *frustrado*, *satisfeito*, *animado*, *gentil*, *indelicado*, *triste* e *compreensivo*. O serviço detecta esses tons do texto de uma conversa entre um cliente e um agente. Os tons são atualmente uma funcionalidade beta.
-   A IBM liberou atualizações para o modelo de pontuação do tom de emoção que melhoram os resultados de emoção.

### 15 de março de 2017
{: #March2017}

A IBM atualizou o modelo de pontuação do tom de emoção. O conjunto de dados de treinamento foi expandido. Como resultado, os modelos agora têm maior precisão no conjunto de dados da referência.

### 1 de dezembro de 2016
{: #December2016}

A IBM atualizou as pontuações de tom de emoção do documento. O novo modelo leva em conta o perfil de emoção de sentenças para agregar a pontuação do documento.

### 18 de outubro de 2016
{: #October2016b}

A IBM aprimorou o tom social. O serviço agora usa técnica de integração de palavra de software livre chamada [GloVe ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://nlp.stanford.edu/projects/glove/){: new_window} para inferir pontuações de tom social. Essa mudança permite que o serviço cubra um vocabulário maior de palavras ao calcular tons sociais. Para obter mais informações sobre como os tons sociais são inferidos, consulte [A ciência por trás do serviço](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) para o serviço do {{site.data.keyword.personalityinsightsshort}}.

### 3 de outubro de 2016
{: #October2016a}

A IBM aprimorou a detecção de emoção no nível da sentença. O serviço usa novos dados de treinamento, um novo processo de seleção de recurso e maiores léxicos de palavras, emojis e gírias. Essas mudanças produzem pontuações de emoção diferentes, mas significativamente melhoradas, no nível da sentença. A API do serviço não mudou.

### 19 de maio de 2016
{: #May2016}

A liberação generally available (GA) do serviço do {{site.data.keyword.toneanalyzershort}} inclui estes novos recursos:

-   Os modelos de serviço usam sensibilidade de contexto melhorada para interpretar o tom. Os modelos agora usam mais do que apenas tokens lexicais. Eles agora consideram recursos adicionais, como pontuação, emoticons, parâmetros de linguagem, como estrutura de sentença, e a complexidade da sentença.
-   O modelo de tom de composição foi renomeado para tom de linguagem.
-   Os modelos de tom de linguagem e de emoção agora lidam com negações.
-   O serviço não mais retorna uma resposta para sentenças com menos de três palavras.
-   O serviço agora tem uma demo simplificada e melhorada do [ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://tone-analyzer-demo.mybluemix.net){: new_window}.
