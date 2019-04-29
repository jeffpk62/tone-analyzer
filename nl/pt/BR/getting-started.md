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
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Tutorial Introdução
{: #gettingStarted}

O serviço do {{site.data.keyword.toneanalyzershort}} analisa o tom do conteúdo de entrada. Este tutorial mostra comandos que analisam diferentes conteúdos de amostra. Os exemplos demonstram os terminais de uso geral e de engajamento do cliente.
{: shortdesc}

O tutorial usa as chaves de API do {{site.data.keyword.cloud}} Identity and Access Management (IAM) para autenticação. As instâncias de serviço mais antigas podem continuar a usar o `{username}` e a `{password}` de suas credenciais de serviço existentes do Cloud Foundry para autenticação. Autentique usando a abordagem certa para sua instância de serviço. Para obter mais informações sobre o uso do serviço de autenticação do IAM, veja as [Notas sobre a liberação](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
{: important}

## Antes de Começar
{: #prerequisites}

- {: hide-dashboard}  Crie uma instância do serviço:
    1.  {: hide-dashboard} Acesse a página do[{{site.data.keyword.toneanalyzershort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} no Catálogo do {{site.data.keyword.cloud_notm}}.
    1.  {: hide-dashboard} Inscreva-se para uma conta grátis do {{site.data.keyword.cloud_notm}} ou efetue login.
    1.  {: hide-dashboard} Clique em **Criar**.
-   Copie as credenciais para autenticação em sua instância de serviço:
    1.  {: hide-dashboard} No painel do [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/dashboard/apps){: new_window}, clique em sua instância de serviço do {{site.data.keyword.toneanalyzershort}} para acessar a página do painel do serviço {{site.data.keyword.toneanalyzershort}}.
    1.  Na página **Gerenciar**, clique em **Mostrar** para visualizar suas credenciais.
    1.  Copie os valores `API Key` e `URL`.
-   Certifique-se de ter o comando `curl`.
    -   Os exemplos usam o comando `curl` para chamar métodos da interface HTTP. Instale a versão para seu sistema operacional de [curl.haxx.se ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://curl.haxx.se/){: new_window}. Instale a versão que suporta o protocolo Secure Sockets Layer (SSL). Certifique-se de incluir o arquivo binário instalado em sua variável de ambiente `PATH`.

Ao inserir um comando, substitua `{apikey}` e `{url}` por sua chave de API e URL reais. Omita as chaves, as quais indicam um valor de variável, do comando. Um valor real se assemelha ao exemplo a seguir:
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## Etapa 1: Usando o terminal de uso geral por meio do método de solicitação POST
{: #generalPurposePost}

Os comandos a seguir chamam o método `POST /v3/tone` para analisar o conteúdo do arquivo `tone.json`. O arquivo inclui um único parágrafo de texto simples que é escrito por uma pessoa. Os exemplos demonstram os parâmetros de consulta `sentences` do método.

1.  Faça download do arquivo de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a>.
1.  Emita o comando a seguir para analisar o tom do conteúdo geral e de cada sentença individual.
    -   {: hide-dashboard} Substitua `{apikey}` e `{url}` por suas informações.
    -   Modifique `{path_to_file}` para especificar o local do arquivo `tone.json`.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  Emita o comando a seguir para analisar somente o tom do conteúdo geral configurando o parâmetro `sentences` para `false`.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

Para obter um exemplo da saída do método, consulte [Resposta de exemplo](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone).

## Etapa 2: Usando o terminal de uso geral por meio do método de solicitação GET
{: #generalPurposeGet}

A interface também oferece um método `GET /v3/tone`. O método `GET` fornece a mesma funcionalidade e produz os mesmos resultados que o método `POST`, mas você usa o parâmetro de consulta `text` do método para especificar o conteúdo a ser analisado. O método aceita somente entrada de texto sem formatação.

1.  O exemplo a seguir especifica o texto do arquivo `tone.json` por meio do parâmetro `text`; conforme mostrado, deve-se codificar o texto por URL. O comando omite o parâmetro `sentences`, portanto, retorna a mesma saída que o primeiro exemplo de `POST` mostrado anteriormente. (O exemplo inclui quebras de linha para capacidade de leitura; não as inclua em um comando real.)

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## Etapa 3: Usando o terminal de engajamento do cliente
{: #customerEngagement}

O comando a seguir chama o método `POST /v3/tone_chat` para analisar o conteúdo do arquivo `tone-chat.json`. O arquivo inclui uma breve troca de mensagens entre duas pessoas, um <code>customer</code> e um <code>agent</code>.

1.  Faça download do arquivo de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a>.
1.  Emita o comando a seguir para analisar o tom da troca no arquivo de amostra.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

A resposta do serviço indica os tons mais predominantes que são detectados para cada elocução da entrada. Para visualizar o conteúdo da resposta para essa solicitação, consulte [Exemplo de resposta](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat).

## Etapas Seguintes
{: #gsns}

-   Para obter mais informações sobre o método `/v3/tone`, veja [Usando o terminal de uso geral](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe).
-   Para obter mais informações sobre o método `/v3/tone_chat`, veja [Usando o terminal de engajamento do cliente](/docs/services/tone-analyzer?topic=tone-analyzer-utco).
-   Para obter mais informações sobre os métodos da interface do serviço, veja a [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
