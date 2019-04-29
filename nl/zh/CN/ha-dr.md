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

# 高可用性和灾难恢复
{: #ha-dr}

{{site.data.keyword.toneanalyzerfull}} 服务在任何 {{site.data.keyword.cloud_notm}} 位置均高度可用。它没有针对灾难恢复的备份和复原需求。
{: shortdesc}

## 高可用性
{: #high-availability}

{{site.data.keyword.toneanalyzershort}} 服务在任何 {{site.data.keyword.cloud_notm}} 位置（例如，达拉斯或华盛顿特区）中均高度可用，无单点故障。服务借助于 {{site.data.keyword.cloud_notm}} 提供的多专区区域 (MZR) 功能，自动且透明地实现高可用性。

{{site.data.keyword.cloud_notm}} 支持不在单个位置中分担单点故障的多个专区。它还在区域中的各个专区之间提供自动负载均衡。

## 灾难恢复
{: #disaster-recovery}

{{site.data.keyword.toneanalyzershort}} 服务无状态。它不在 {{site.data.keyword.cloud_notm}} 上存储用户数据。如果某个区域中发生灾难性故障，请完成以下步骤：

1.  在不同区域中创建 {{site.data.keyword.toneanalyzershort}} 服务的新实例。
1.  修改应用程序以使用新服务实例的 URL 和凭证。
