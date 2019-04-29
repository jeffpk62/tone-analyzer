---

copyright:
  years: 2019
lastupdated: "2019-03-19"

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

# Alta disponibilidade e recuperação de desastre
{: #ha-dr}

O serviço {{site.data.keyword.toneanalyzerfull}} está altamente disponível dentro de qualquer local do {{site.data.keyword.cloud_notm}}. Ele não tem requisitos de backup e restauração para recuperação de desastre.
{: shortdesc}

## Alta disponibilidade
{: #high-availability}

O serviço {{site.data.keyword.toneanalyzershort}} está altamente disponível sem nenhum ponto único de falha dentro de qualquer local do {{site.data.keyword.cloud_notm}} (por exemplo, Dallas ou Washington, DC). O serviço alcança alta disponibilidade de forma automática e transparente por meio do recurso de região multizona (MZR) fornecido pelo {{site.data.keyword.cloud_notm}}.

O {{site.data.keyword.cloud_notm}} permite múltiplas zonas que não compartilham um
ponto único de falha dentro de um único local. Ele também fornece balanceamento automático de carga
entre as zonas dentro de uma região.

## Recuperação de desastre
{: #disaster-recovery}

O serviço {{site.data.keyword.toneanalyzershort}} é stateless. Ele não armazena dados
do usuário no {{site.data.keyword.cloud_notm}}. No caso de uma falha catastrófica em uma região,
conclua as etapas a seguir:

1.  Crie uma nova instância do serviço {{site.data.keyword.toneanalyzershort}} em uma região diferente.
1.  Modifique seu aplicativo para usar a URL e as credenciais para a nova instância de serviço.
