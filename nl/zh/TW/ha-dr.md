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

# 高可用性及災難回復
{: #ha-dr}

在任何 {{site.data.keyword.cloud_notm}} 位置內，{{site.data.keyword.toneanalyzerfull}} 服務都高度可用。它沒有災難回復的備份及還原需求。
{: shortdesc}

## 高可用性
{: #high-availability}

在任何 {{site.data.keyword.cloud_notm}} 位置（例如，達拉斯或華盛頓特區）內，{{site.data.keyword.toneanalyzershort}} 服務都高度可用，且沒有單一失敗點。此服務會透過 {{site.data.keyword.cloud_notm}} 所提供的多區域地區 (MZR) 特性，自動且透通地達到高可用性。

{{site.data.keyword.cloud_notm}} 會啟用未在單一位置內共用單一失敗點的多個區域。它也會提供地區內區域之間的自動載入平衡。

## 災難回復
{: #disaster-recovery}

{{site.data.keyword.toneanalyzershort}} 服務是無狀態的。它不會將使用者資料儲存至 {{site.data.keyword.cloud_notm}}。如果地區中發生災難性失效，則請完成下列步驟：

1.  在不同的地區中，建立新的 {{site.data.keyword.toneanalyzershort}} 服務實例。
1.  修改應用程式，以使用新服務實例的 URL 及認證。
