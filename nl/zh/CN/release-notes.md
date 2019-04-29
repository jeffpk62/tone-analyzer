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

# 发行说明
{: #rnrn}

以下各节记录了对 {{site.data.keyword.toneanalyzershort}} 服务的每个发行版包含的新增功能和更改。这些更改不会中断现有代码。
{: shortdesc}

发行说明记录每个更新的*服务版本*和*接口版本*。您可以指定带有 `version` 查询参数的*接口版本*，以使用该更新提供的新特性和功能。此服务将返回带有 `X-Service-Api-Version` 响应头的两个版本。
{: note}

## 2019 年 2 月 22 日
{: #February2019}

**服务版本** - `3.5.9`<br/> **接口版本** - `2017-09-21`

-   现在，{{site.data.keyword.cloud}} 法兰克福位置 (**eu-de**) 中的 {{site.data.keyword.toneanalyzershort}} 服务使用基于令牌的 Identity and Access Management (IAM) 认证。在此或任何位置中创建的所有新服务实例都使用 IAM 认证。
-   还针对内部更改和改进更新了服务。

## 2018 年 11 月 18 日
{: #November2018b}

**服务版本** - `3.5.4`<br/> **接口版本** - `2017-09-21`

现在，在 {{site.data.keyword.cloud_notm}} 伦敦位置 (**eu-gb**) 提供了 {{site.data.keyword.toneanalyzershort}} 服务。与所有位置一样，伦敦使用基于令牌的 IAM 认证。在此位置中创建的所有新服务实例都使用 IAM 认证。

## 2018 年 11 月 7 日
{: #November2018a}

**服务版本** - `3.5.4`<br/> **接口版本** - `2017-09-21`

现在，在 {{site.data.keyword.cloud_notm}} 东京位置 (**jp-tok**) 中提供了 {{site.data.keyword.toneanalyzershort}} 服务。与所有位置一样，东京使用基于令牌的 IAM 认证。在此位置中创建的所有新服务实例都使用 IAM 认证。

## 较早的发行版
{: #rnor}

  - [2018 年 10 月 30 日](#30-october-2018)
  - [2018 年 6 月 11 日](#11-june-2018)
  - [2018 年 5 月 25 日](#25-may-2018)
  - [2018 年 3 月 13 日](#13-march-2018)
  - [2017 年 9 月 28](#28-september-2017)
  - [2017 年 9 月 25](#25-september-2017)
  - [2017 年 7 月 6](#6-july-2017)
  - [2017 年 7 月 1 日](#1-july-2017)
  - [2017 年 5 月 8 日](#8-may-2017)
  - [2017 年 4 月 17 日](#17-april-2017)
  - [2017 年 3 月 15 日](#15-march-2017)
  - [2016 年 12 月 1 日](#1-december-2016)
  - [2016 年 10 月 18 日](#18-october-2016)
  - [2016 年 10 月 3 日](#3-october-2016)
  - [2016 年 5 月 19 日](#19-may-2016)

### 2018 年 10 月 30 日
{: #October2018}

**服务版本** - `3.5.4`<br/> **接口版本** - `2017-09-21`

对于所有位置，{{site.data.keyword.toneanalyzershort}} 服务已迁移至基于令牌的 IAM 认证。所有 {{site.data.keyword.cloud_notm}} 服务现在都使用 IAM 认证。在以下日期，迁移每个位置中的 {{site.data.keyword.toneanalyzershort}} 服务：

-   达拉斯 (**us-south**)：2018 年 10 月 30 日
-   法兰克福 (**eu-de**)：正在进行中
-   华盛顿特区 (**us-east**)：2018 年 6 月 11 日
-   悉尼 (**au-syd**)：2018 年 5 月 25 日

在法兰克福位置，服务继续使用 Cloud Foundry 服务凭证进行认证。此位置将尽快迁移至 IAM 认证。
{: important}

迁移至 IAM 认证会以不同方式影响新的服务实例和现有服务实例：

-   *在任何位置创建的所有新服务实例*现在都使用 IAM 认证来访问服务。您可以传递不记名令牌或 API 密钥：令牌支持已认证的请求，而无需在每个调用中嵌入服务凭证；API 密钥使用 HTTP 基本认证。使用任何 {{site.data.keyword.watson}} SDK 时，都可以传递 API 密钥，并让 SDK 管理令牌的生命周期。
-   *在指示的迁移日期之前在位置中创建的现有服务实例*继续使用来自先前 Cloud Foundry 服务凭证的 `{username}` 和 `{password}` 进行认证，直至更新为使用 IAM 认证。因为 {{site.data.keyword.toneanalyzershort}} 服务无状态，因此可以执行以下步骤以将现有服务实例转换为使用 IAM 认证：

    1.  删除并重新创建服务实例。
    1.  修改应用程序代码以使用 IAM 认证。

有关更多信息，请参阅以下文档：

-   要了解服务实例使用的认证机制，请通过单击 [{{site.data.keyword.cloud_notm}} 仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/dashboard/apps){: new_window} 上的实例以查看服务凭证。
-   有关将 IAM 令牌与 Watson 服务配合使用的更多信息，请参阅[使用 IAM 令牌进行认证](/docs/services/watson?topic=watson-iam)。
-   有关将 IAM API 密钥与 Watson 服务配合使用的更多信息，请参阅 [IAM 服务 API 密钥](/docs/services/watson?topic=watson-api-key-bp)。
-   有关使用 IAM 认证的示例，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/tone-analyzer){: new_window}。


### 2018 年 6 月 11 日
{: #June2018}

**服务版本** - `3.5.4`<br/> **接口版本** - `2017-09-21`

对于在华盛顿特区 (**us east**) 中托管的服务实例和应用程序，服务现在支持新的 API 认证过程。有关更多信息，请参阅 [2018 年 10 月 30 日服务更新](#October2018)。

### 2018 年 5 月 25 日
{: #May2018}

**服务版本** - `3.5.4`<br/> **接口版本** - `2017-09-21`

对于在悉尼 (**au-syd**) 中托管的服务实例和应用程序，服务现在支持新的 API 认证过程。有关更多信息，请参阅 [2018 年 10 月 30 日服务更新](#October2018)。

### 2018 年 3 月 13 日
{: #March2018}

**服务版本** - `3.5.3`<br/> **接口版本** - `2017-09-21`

服务已更新，对于客户参与端点 `/v3/tone_chat`，除英语外，还添加了法语 (`fr`) 输入内容。使用 `Content-Language` 请求头指定语言；缺省为美国英语。

### 2017 年 9 月 28
{: #September2017b}

**服务版本** - `3.4.1`<br/> **接口版本** - `2017-09-21`

单个 {{site.data.keyword.cloud_notm}} 用户名可提交的最大请求数的调速限制增加为 1200 个请求/分钟。如果用户超过该限制，那么服务将返回 HTTP 响应代码 429 *请求过多*。

### 2017 年 9 月 25
{: #September2017a}

**服务版本** - `3.4.1`<br/> **接口版本** - `2017-09-21`

-   通用端点（`/v3/tone` 方法）已更改。

    -   除英语外，还支持法语 (`fr`) 输入内容。
    -   不再返回社交语气。
    -   返回的情绪语气中不再包含 `disgust`。
    -   省略任何分数小于 `0.5` 的语气。此限定条件与 `/v3/tone_chat` 方法的响应匹配。
    - 不再返回语气类别（`tone_categories` 字段）作为其输出的一部分。值满足符合条件阈值的所有语气都将作为单个 `tones` 对象的一部分返回。与以前一样，缺省情况下，始终会返回完整文档和每个单独句子的语气。
    - 不再接受 `tones` 查询参数，以限制指定语气的输出。每个请求都会返回所有符合条件的语气。请求中附带该参数不会导致错误，但它对响应没有影响。
    - 对于单个句子，不再返回 `input_from` 和 `input_to` 字段。除了分析结果外，该方法现在仅返回每个句子的标识和文本。

-   在下列情况下，服务现在将返回 HTTP 响应代码 200（而不是 400）以表示部分正确输入：

    -   对于 `/v3/tone` 方法，如果您提交的输入内容超过 128 KB 或 1000 个句子，那么服务会返回 `warning` 字段作为其响应的一部分。对于文档级别的分析，该服务分析前 1000 个句子。对于句子级别的分析，则仅分析前 100 个句子。如果超过任一限制，那么服务的较早版本将针对请求返回响应代码 400。服务现在还分析少于三个字的句子。
    -   对于 `/v3/tone_chat` 方法，如果提交的话语超过 50 个，那么对于整体内容，此服务将在响应的 `utterances_tone` 级别返回 `warning` 字段，且仅分析前 50 个话语。如果提交包含超过 500 个字符的单一话语，那么该服务将针对该话语返回 `error` 字段，并且不会分析该话语。如果超过任一限制，那么服务的较早版本将返回响应代码 400。如果输入的所有话语超过 500 个字符，那么该服务仍会针对该请求返回响应代码 400。

-   该服务现在对从单个用户接受的请求数进行了控制。如果每分钟从单个 {{site.data.keyword.cloud_notm}} 用户名收到超过 600 个请求，那么该服务将返回 HTTP 响应代码 429 *请求过多*。

-   以下更改适用于通用端点和客户参与端点：

    -   使用 `version` 参数指定的接口版本为 `2017-09-21`，以使用服务的最新版本。
    -   文档已更新，以说明该服务可以生成各种语言的本地化输出。使用 `Accept-Language` 请求头来指定语言。

### 2017 年 7 月 6
{: #July2017b}

**服务版本** - `3.3.6`<br/> **接口版本** - `2016-05-19`

该服务已更新，对客户参与端点进行了小型缺陷修订。

### 2017 年 7 月 1
{: #July2017a}

**服务版本** - `3.3.5`<br/> **接口版本** - `2016-05-19`

{{site.data.keyword.toneanalyzershort}} 服务的客户参与端点现在为一般可用 (GA) 版本。对端点的所有调用现在都按与通用端点调用相同的费率进行收费。

### 2017 年 5 月 8
{: #May2017}

**服务版本** - `3.3.4`<br/> **接口版本** - `2016-05-19`

IBM 通过进一步扩展训练数据集，更新了情绪语气和客户服务参与语气评分模型。模型现在对基准数据集具有更高的精度。

### 2017 年 4 月 17
{: #April2017}

-   现在提供特定于客户参与领域的一组新语气：*沮丧*、*满意*、*兴奋*、*有礼*、*粗鲁*、*悲伤*和*同情*。该服务将从客户与代理之间的对话文本中检测这些语气。这些语气目前是 beta 功能。
-   IBM 发布了对情绪语气评分模型的更新，该模型改进了情绪结果。

### 2017 年 3 月 15
{: #March2017}

IBM 更新了情绪语气评分模型。扩展了训练数据集。因此，模型现在对基准数据集具有更高的精度。

### 2016 年 12 月 1
{: #December2016}

IBM 更新了文档情绪语气评分。新模型会考虑句子的情绪概要信息，以汇总文档分数。

### 2016 年 10 月 18
{: #October2016b}

IBM 增强了社交语气。该服务现在使用称为 [GloVe ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://nlp.stanford.edu/projects/glove/){: new_window} 的开放式源代码字嵌入技术来推断社交语气得分。此更改允许服务在计算社交语气时涵盖较大量的词汇。有关如何推断社交语气的更多信息，请参阅 {{site.data.keyword.personalityinsightsshort}} 服务的[服务背后的科学](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html)。

### 2016 年 10 月 3
{: #October2016a}

IBM 增强了句子级别的情绪检测。该服务使用新的训练数据、新的特点选择过程，以及文字、表情符号和俚语的扩充词典。这些更改会产生不同的结果，但在句子级别却大幅提高了情绪分数。该服务的 API 未更改。

### 2016 年 5 月 19 日
{: #May2016}

{{site.data.keyword.toneanalyzershort}} 服务的一般可用 (GA) 发行版包括以下新增功能：

-   服务的模型使用改进的上下文灵敏度来解释语气。现在，这些模型不仅仅使用词汇标记。他们现在考虑使用标点、表情符号、语言参数（如句子结构）和句子复杂性等特点。
-   书写语气模型已重命名为语言语气。
-   语言和情绪语气模型现在处理否定词。
-   该服务不再返回少于三个字的句子的响应。
-   现在，该服务有已简化并改进的[演示 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://tone-analyzer-demo.ng.bluemix.net){: new_window}。
