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

# 高可用性および災害復旧
{: #ha-dr}

{{site.data.keyword.toneanalyzerfull}} サービスは、 {{site.data.keyword.cloud_notm}} のどこでも、高い可用性があります。このサービスは災害復旧に対するバックアップやリストアの要件がありません。
{: shortdesc}

## 高可用性
{: #high-availability}

{{site.data.keyword.toneanalyzershort}} サービスは、{{site.data.keyword.cloud_notm}} のどの場所においても (例えばダラスであろうと、ワシントン DC であろうと) 単一障害点のない、高可用性サービスです。このサービスが高可用性を自動的に、そして容易に実現しているのは、{{site.data.keyword.cloud_notm}} が提供する複数ゾーン領域 (MZR) 機能によるものです。

{{site.data.keyword.cloud_notm}} では、単一ロケーション内で単一障害点を共有しない、複数ゾーンの構築が可能です。また、1 領域内の複数ゾーンにわたる自動ロード・バランシングも提供します。

## 災害復旧
{: #disaster-recovery}

{{site.data.keyword.toneanalyzershort}} サービスはステートレスです。 {{site.data.keyword.cloud_notm}} 上にユーザー・データを保管しません。領域内で大規模な障害が発生した場合は、以下の手順を実行してください。

1.  別の領域に {{site.data.keyword.toneanalyzershort}} サービスの新しいインスタンスを作成します。
1.  新しいサービス・インスタンスの URL と資格情報を使用するように、アプリケーションを変更します。
