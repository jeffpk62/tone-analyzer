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

# Notas sobre a liberação
{: #rnrn}

As seções a seguir documentam os novos recursos e as mudanças que foram incluídas em cada liberação do serviço do {{site.data.keyword.toneanalyzershort}}. As mudanças não quebram o código existente.
{: shortdesc}

As notas sobre a liberação documentam a *versão do serviço* e a *versão da interface* para cada atualização. Você especifica a *versão da interface* com o parâmetro de consulta `version` para usar novos recursos e funcionalidades disponibilizados com esta atualização. O serviço retorna ambas as versões com o cabeçalho de resposta `X-Service-Api-Version`.
{: note}

## 22 de fevereiro de 2019
{: #February2019}

**Versão do serviço** - `3.5.9`<br/> **Versão da interface** - `2017-09-21`

-   O serviço {{site.data.keyword.toneanalyzershort}} no local Frankfurt do {{site.data.keyword.cloud}} (**eu-de**) agora usa a autenticação
do Identity and Access Management (IAM) baseada em token. Todas as novas instâncias de serviços que você cria nesse ou em qualquer local usam a autenticação do IAM.
-   O serviço também foi atualizado para mudanças e melhorias internas.

## 18 de novembro de 2018
{: #November2018b}

**Versão do serviço** - `3.5.4`<br/> **Versão da interface** - `2017-09-21`

O serviço {{site.data.keyword.toneanalyzershort}} agora está disponível no local Londres do {{site.data.keyword.cloud_notm}} (**eu-gb**). Como todos os
locais, Londres usa a autenticação do IAM baseada em token. Todas as novas instâncias de serviços que você cria nesse local usam a autenticação do IAM.

## 7 de novembro de 2018
{: #November2018a}

**Versão do serviço** - `3.5.4`<br/> **Versão da interface** - `2017-09-21`

O serviço {{site.data.keyword.toneanalyzershort}} agora está disponível no local Tokyo do {{site.data.keyword.cloud_notm}} (**jp-tok**). Como todos os
locais, Tokyo usa a autenticação do IAM baseada em token. Todas as novas instâncias de serviços que você cria nesse local usam a autenticação do IAM.

## Liberações mais antigas
{: #rnor}

  - [30 de outubro de 2018](#30-october-2018)
  - [11 de junho de 2018](#11-june-2018)
  - [25 de maio de 2018](#25-may-2018)
  - [13 de março de 2018](#13-march-2018)
  - [28 de setembro de 2017](#28-september-2017)
  - [25 de setembro de 2017](#25-september-2017)
  - [6 de julho de 2017](#6-july-2017)
  - [1 de julho de 2017](#1-july-2017)
  - [8 de maio de 2017](#8-may-2017)
  - [17 de abril de 2017](#17-april-2017)
  - [15 de março de 2017](#15-march-2017)
  - [1 de dezembro de 2016](#1-december-2016)
  - [18 de outubro de 2016](#18-october-2016)
  - [3 de outubro de 2016](#3-october-2016)
  - [19 de maio de 2016](#19-may-2016)

### 30 de outubro de 2018
{: #October2018}

**Versão do serviço** - `3.5.4`<br/> **Versão da interface** - `2017-09-21`

O serviço {{site.data.keyword.toneanalyzershort}} migrou para a autenticação do IAM
baseada em token para todos os locais. Todos os serviços do {{site.data.keyword.cloud_notm}} agora
usam a autenticação do IAM. O serviço {{site.data.keyword.toneanalyzershort}} foi migrado em
cada local nas datas a seguir:

-   Dallas (**us-south**): 30 de outubro de 2018
-   Frankfurt (**eu-de**): em andamento
-   Washington, DC (**us-east**): 11 de junho de 2018
-   Sydney (**au-syd**): 25 de maio de 2018

O serviço continua a usar as credenciais de serviço do Cloud Foundry para autenticação no local Frankfurt. Esse local será migrado para a autenticação do IAM assim que possível.
{: important}

A migração para a autenticação do IAM afeta instâncias de serviço novas e existentes de
maneira diferente:

-   *Todas as novas instâncias de serviço que você cria em qualquer local* agora
usam a autenticação do IAM para acessar o serviço. É possível passar um token de acesso ou uma chave
de API: os tokens suportam solicitações autenticadas sem a integração de credenciais de serviço em
cada chamada; as chaves de API usam a autenticação básica HTTP. Quando você usa qualquer um dos SDKs
do {{site.data.keyword.watson}}, pode passar a chave da API e deixar o SDK gerenciar o ciclo
de vida dos tokens.
-   *As instâncias de serviço existentes que você criou em um local antes da data
de migração indicada* continuam a usar o `{username}` e a `{password}`
de suas credenciais de serviço do Cloud Foundry anteriores para autenticação até que você as atualize
para usar a autenticação do IAM. Como o serviço {{site.data.keyword.toneanalyzershort}} é
stateless, é possível executar as etapas a seguir para converter uma instância de serviço existente
para usar a autenticação do IAM:

    1.  Excluir e recriar a instância do serviço.
    1.  Modificar seu código do aplicativo para usar a autenticação do IAM.

Para obter mais informações, veja a documentação a seguir:

-   Para saber qual mecanismo de autenticação sua instância de serviço usa, visualize suas
credenciais de serviço clicando na instância no painel do [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/dashboard/apps){: new_window}.
-   Para obter mais informações sobre o uso de tokens do IAM com serviços do Watson, veja [Autenticando com tokens do IAM](/docs/services/watson?topic=watson-iam).
-   Para obter mais informações sobre o uso de chaves de API do IAM com serviços do Watson,
veja [Chaves de API de serviço do IAM](/docs/services/watson?topic=watson-api-key-bp).
-   Para obter exemplos que usam a autenticação do IAM, veja a [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

### 11 de junho de 2018
{: #June2018}

**Versão do serviço** - `3.5.4`<br/> **Versão da interface** - `2017-09-21`

Para instâncias de serviço e aplicativos que estão hospedados em Washington, DC
(**us east**), o serviço agora suporta um novo processo de autenticação
de API. Para obter mais informações, veja a [atualização de serviço
de 30 de outubro de 2018](#October2018).

### 25 de maio de 2018
{: #May2018}

**Versão do serviço** - `3.5.4`<br/> **Versão da interface** - `2017-09-21`

Para instâncias de serviço e aplicativos que estão hospedados em Sydney (**au-syd**), o serviço agora suporta um novo processo de autenticação de API. Para obter mais informações, veja a [atualização de serviço
de 30 de outubro de 2018](#October2018).

### 13 de março de 2018
{: #March2018}

**Versão do serviço** - `3.5.3`<br/> **Versão da interface** - `2017-09-21`

O serviço foi atualizado para incluir o conteúdo de entrada em francês (`fr`),
além do inglês para o terminal de engajamento do cliente, `/v3/tone_chat`. Você usa
o cabeçalho da solicitação `Content-Language` para especificar um idioma; o padrão é
inglês dos EUA.

### 28 de setembro de 2017
{: #September2017b}

**Versão do serviço** - `3.4.1`<br/> **Versão da interface** - `2017-09-21`

O limite no número máximo de solicitações que um nome do usuário individual do {{site.data.keyword.cloud_notm}} pode enviar aumentou para 1.200 solicitações por minuto. O serviço retornará o código de resposta HTTP 429 *Muitas solicitações* se um usuário exceder esse limite.

### 25 de setembro de 2017
{: #September2017a}

**Versão do serviço** - `3.4.1`<br/> **Versão da interface** - `2017-09-21`

-   O terminal de uso geral (o método `/v3/tone`) mudou.

    -   Suporta conteúdo de entrada em francês (`fr`) além do inglês.
    -   Não retorna mais tons sociais.
    -   Não retorna mais `disgust` com os tons de emoção.
    -   Omite qualquer tom cuja pontuação seja menor que `0,5`. Essa qualificação corresponde à resposta do método `/v3/tone_chat`.
    - Já não retorna categorias de tom (o campo `tone_categories`) como parte da saída. Todos os tons cujos valores cumprem o limite de qualificação são retornados como parte de um único objeto `tones`. Como antes, os tons são sempre retornados para o documento completo e para cada sentença individual por padrão.
    - Não mais aceita um parâmetro de consulta `tones` para limitar a saída para tons especificados. Todos os tons de qualificação são retornados para cada solicitação. Incluir o parâmetro com uma solicitação não causa um erro, mas não tem nenhum efeito na resposta.
    - Não mais retorna os campos `input_from` e `input_to` para sentenças individuais. Além dos resultados de sua análise, o método agora retorna apenas um ID e o texto de cada sentença.

-   O serviço agora retorna o código de resposta HTTP 200 em vez de 400 para uma entrada parcialmente correta nos casos a seguir:

    -   Para o método `/v3/tone`, se você enviar mais de 128 KB ou 1000 sentenças de conteúdo de entrada, o serviço retornará um campo `warning` como parte de sua resposta. O serviço analisa as primeiras 1.000 sentenças para análise no nível do documento. Ele analisa somente as primeiras 100 sentenças para análise no nível de sentença. Versões anteriores do serviço retornavam o código de resposta 400 para a solicitação se você excedesse qualquer um dos dois limites. Além disso, o serviço agora analisa sentenças que têm menos de três palavras.
    -   Para o método `/v3/tone_chat`, se você enviar mais de 50 elocuções, o serviço retornará um campo `warning` para o conteúdo geral b= no nível de `utterances_tone` da resposta; ele analisa apenas as primeiras 50 elocuções. Se você enviar uma única elocução com mais de 500 caracteres, o serviço retornará um campo `error` para essa elocução e não a analisará. Versões anteriores do serviço retornavam o código de resposta 400 se você excedesse qualquer um dos dois limites. Se todos as elocuções da entrada tiverem mais de 500 caracteres, o serviço ainda retornará o código de resposta 400 para a solicitação.

-   O serviço agora regula o número de solicitações que aceita de um único usuário. O serviço retornará o código de resposta HTTP 429 *Muitas solicitações* se receber mais de 600 solicitações por minuto de um nome do usuário individual do {{site.data.keyword.cloud_notm}}.

-   As mudanças a seguir se aplicam aos terminais de uso geral e de engajamento do cliente:

    -   A versão da interface que é especificada com o parâmetro `version` é `2017-09-21` para usar a versão mais recente do serviço.
    -   A documentação foi atualizada para observar que o serviço pode produzir a saída
localizada em vários idiomas. Use o cabeçalho da solicitação `Accept-Language` para
especificar o idioma.

### 6 de julho de 2017
{: #July2017b}

**Versão do serviço** - `3.3.6`<br/> **Versão da interface** - `2016-05-19`

O serviço foi atualizado para uma correção de defeito pequeno para o terminal de engajamento do cliente.

### 1 de julho de 2017
{: #July2017a}

**Versão do serviço** - `3.3.5`<br/> **Versão da interface** - `2016-05-19`

O terminal de engajamento do cliente do serviço do {{site.data.keyword.toneanalyzershort}} agora
está geralmente disponível (GA). Todas as chamadas para o terminal agora são cobradas na mesma taxa que as chamadas para o terminal de uso geral.

### 8 de maio de 2017
{: #May2017}

**Versão do serviço** - `3.3.4`<br/> **Versão da interface** - `2016-05-19`

A IBM atualizou os modelos de pontuação do tom de emoção e do tom de engajamento de atendimento ao cliente expandindo ainda mais o conjunto de dados de treinamento. Os modelos agora têm maior precisão no conjunto de dados da referência.

### 17 de abril de 2017
{: #April2017}

-   Um novo conjunto de tons específicos para o domínio de engajamento do cliente está
agora disponível: *frustrado*, *satisfeito*, *animado*,
*educado*, *grosseiro*, *triste* e *compreensivo*. O serviço detecta esses tons do texto de uma conversa entre um cliente e um agente. Os tons são atualmente uma funcionalidade beta.
-   A IBM liberou atualizações para o modelo de pontuação do tom de emoção que melhoram os resultados de emoção.

### 15 de março de 2017
{: #March2017}

A IBM atualizou o modelo de pontuação do tom de emoção. O conjunto de dados de treinamento foi expandido. Como resultado, os modelos agora têm maior precisão no conjunto de dados da referência.

### 1 de dezembro de 2016
{: #December2016}

A IBM atualizou as pontuações de tom de emoção do documento. O novo modelo considera o
perfil de emoção das sentenças para agregar a pontuação do documento.

### 18 de outubro de 2016
{: #October2016b}

A IBM aprimorou o tom social. O serviço agora usa uma técnica de integração de palavras de
software livre que é chamada [GloVe ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://nlp.stanford.edu/projects/glove/){: new_window} para deduzir pontuações de tom social. Essa mudança
permite que o serviço abranja um vocabulário maior de palavras quando ele calcula os tons sociais. Para obter mais informações sobre como os tons sociais são inferidos, consulte [A ciência por trás do serviço](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) para o serviço do {{site.data.keyword.personalityinsightsshort}}.

### 3 de outubro de 2016
{: #October2016a}

A IBM aprimorou a detecção de emoção no nível da sentença. O serviço usa novos dados de treinamento, um novo processo de seleção de recurso e maiores léxicos de palavras, emojis e gírias. Essas mudanças produzem pontuações de emoção diferentes, mas significativamente melhoradas, no nível da sentença. A API do serviço não mudou.

### 19 de maio de 2016
{: #May2016}

A liberação generally available (GA) do serviço do {{site.data.keyword.toneanalyzershort}} inclui estes novos recursos:

-   Os modelos de serviço usam sensibilidade de contexto melhorada para interpretar o tom. Os
modelos agora usam mais do que tokens lexicais. Eles agora consideram recursos como pontuação, emoticons, parâmetros de linguagem, como estrutura de sentença e complexidade de sentença.
-   O modelo de tom de escrita foi renomeado para tom de linguagem.
-   Os modelos de tom de linguagem e de emoção agora lidam com negações.
-   O serviço não mais retorna uma resposta para sentenças com menos de três palavras.
-   O serviço agora tem uma [demo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://tone-analyzer-demo.ng.bluemix.net){: new_window}.
