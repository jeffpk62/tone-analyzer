---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Tutorial de introdução
{: #gettingStarted}

O serviço do {{site.data.keyword.toneanalyzershort}} analisa o tom do conteúdo de entrada. Este tutorial mostra comandos que analisam diferentes conteúdos de amostra. Os exemplos demonstram o propósito geral e os terminais de engajamento do cliente.
{: shortdesc}

## Antes de Começar
{: #prerequisites}

- Crie uma instância do serviço:
    - {: download} Se você estiver vendo isso, você criou sua instância de serviço. Agora, obtenha suas credenciais.
    - Criar um projeto de um serviço:
        1.  Acesse a página Serviços do {{site.data.keyword.watson}} Developer Console [ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Selecione {{site.data.keyword.toneanalyzershort}}, clique em **Incluir serviços** e inscreva-se para uma conta grátis do {{site.data.keyword.Bluemix_notm}} ou efetue login.
        1.  Digite `tone-tutorial` para o nome do projeto e clique em **Criar projeto**.
- Copie as credenciais para autenticação em sua instância de serviço:
    - {: download} No painel de serviço (o que você está observando):
        1.  Clique na guia **Credenciais de serviço**.
        1.  Clique em **Visualizar credenciais** em **Ações**.
        1.  Copie os valores de `username`, `password` e `url`.
        {: download}
    - Em seu projeto **tone-tutorial** no Developer Console, copie os valores de `username`, `password` e `url` para `"tone_analyzer"` da seção **Credenciais**.
- Certifique-se de que tenha cURL:
    - Os exemplos usam cURL para chamar métodos da interface HTTP. Instale a versão para seu sistema operacional de [curl.haxx.se ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://curl.haxx.se/){: new_window}. Instale a versão que suporta o protocolo Secure Sockets Layer (SSL). Certifique-se de incluir o arquivo binário instalado em sua variável de ambiente `PATH`.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Se você usar o {{site.data.keyword.Bluemix_dedicated_notm}}, crie sua instância de serviço da página [{{site.data.keyword.toneanalyzershort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window}. Para obter detalhes sobre como localizar suas credenciais de serviço, consulte [Credenciais de serviço para serviços do Watson ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Etapa 1: usar o terminal de propósito geral por meio do método de solicitação de POST
{: #generalPurposePost}

Os comandos a seguir chamam o método `POST /v3/tone` para analisar o conteúdo do arquivo `tone.json`. O arquivo inclui um único parágrafo de texto sem formatação escrito por uma pessoa. Os exemplos demonstram os parâmetros de consulta `sentences` do método.

1.  Faça download do arquivo de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.
1.  Emita o comando a seguir para analisar o tom do conteúdo geral e de cada sentença individual.
    -   Substitua `{username}` e `{password}` por suas credenciais de serviço da etapa anterior.
    -   Modifique `{path_to_file}` para especificar o local do arquivo `tone.json`.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  Emita o comando a seguir para analisar somente o tom do conteúdo geral configurando o parâmetro `sentences` para `false`.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

Para obter um exemplo da saída do método, consulte [Resposta de exemplo](/docs/services/tone-analyzer/using-tone.html#exampleResponse).

## Etapa 2: usar o terminal de propósito geral por meio do método de solicitação GET
{: #generalPurposeGet}

A interface também oferece um método `GET /v3/tone`. O método `GET` fornece a mesma funcionalidade e produz os mesmos resultados que o método `POST`, mas você usa o parâmetro de consulta `text` do método para especificar o conteúdo a ser analisado. O método aceita somente entrada de texto sem formatação.

1.  O exemplo a seguir especifica o texto do arquivo `tone.json` por meio do parâmetro `text`; conforme mostrado, deve-se codificar o texto por URL. O comando omite o parâmetro `sentences`, portanto, retorna a mesma saída que o primeiro exemplo de `POST` mostrado anteriormente. (O exemplo inclui quebras de linha para capacidade de leitura; não as inclua em um comando real.)

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## Etapa 3: usar o terminal de engajamento do cliente
{: #customerEngagement}

O comando a seguir chama o método `POST /v3/tone_chat` para analisar o conteúdo do arquivo `tone-chat.json`. O arquivo inclui uma breve troca de mensagens entre duas pessoas, um <code>customer</code> e um <code>agent</code>.

1.  Faça download do arquivo de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.
1.  Emita o comando a seguir para analisar o tom da troca no arquivo de amostra.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

A resposta do serviço indica os tons mais predominantes detectados para cada elocução da entrada. Para visualizar o conteúdo da resposta para essa solicitação, consulte [Exemplo de resposta](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse).

## Próximas Etapas

-   Para obter mais informações sobre o método `/v3/tone`, consulte [Usando o terminal de propósito geral](/docs/services/tone-analyzer/using-tone.html).
-   Para obter mais informações sobre o método `/v3/tone_chat`, consulte [Usando o terminal de engajamento do cliente](/docs/services/tone-analyzer/using-tone-chat.html).
-   Para obter informações detalhadas sobre os métodos da interface de serviço, consulte a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
-   Interaja com a API no [explorador de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window}.
