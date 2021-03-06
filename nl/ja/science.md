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

# サービスを支える科学
{: #ssbts}

{{site.data.keyword.toneanalyzerfull}} サービスは、言語行動と心理学理論の関係を探る研究分野である心理言語学の理論に基づいています。 このサービスは、言語分析を使用するとともに、記述されたテキストの言語特性と感情トーンおよび言語トーンの間の相関関係を基に、それらの両方のトーンのディメンションについてスコアを生成します。
{: shortdesc}

心理言語学の研究者は、人が日常生活で使う言葉が、その人の人格、感じ方、考え方を反映するかどうかを研究しています。数十年に及ぶ研究を経て、今では、言葉はその人が言おうとしていること以外のことも表すということが、心理学やマーケティングなどの分野で受け入れられています。特定の種類の言葉を使用する頻度が、その人の人格、思考スタイル、社会的つながり、感情の状態を知る手掛かりになるのです。

例えば、日常のコミュニケーションは人はさまざまなトーンを表します。楽しい、悲しい、開放的、保守的、分析的、形式張らない、といったトーンがあります ([Gou 他、2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gou)、および [Jian 他、2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-jian))。オンラインでその人のアイデンティティーがどのように受け取られるかや、さまざまな状況でコミュニケーションが有効に働くかどうかは、このようなトーンによって左右されます。

さらに、ビジネス上の E メール・コミュニケーションでは、人はポジティブな感情よりもネガティブな感情を強く感じる傾向があります ([Byron、2008](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-byron))。 そして、ソーシャル・メディアでは、人は他人に与える自分の印象を左右する、さまざまなオンライン・アイデンティティーを表します ([DiMiccoおよび Millen、2007](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-dimicco))。

多くの人は、自然にメッセージを読み、送り手が伝えているトーンを判断します。 しかし、コンピューターが、メッセージに表されているトーンを正確に自動的に検出することができるのでしょうか。 これは、人工知能と認知科学の分野の研究者が答えを見つけようとしている、多くの難問の一つです。最初は {{site.data.keyword.personalityinsightsshort}} サービスで、そして現在は {{site.data.keyword.toneanalyzershort}} サービスで、IBM はこの問題に答えを出そうとしています。

## 関連研究の概要
{: #sorr}

言葉の選択と、人格、感情、態度、内在的な要求、価値観、思考プロセスの間には、統計的に有意な強い相関関係があることが研究によって示されています。 何人かの研究者は、ブログ、エッセイ、ツイートに書くときに特定のカテゴリーの言葉を使う頻度が人によって異なることを発見しました。また、こうしたコミュニケーション・メディアが人格のさまざまな側面を予測するのに役立つことも発見しました。

-   [Fast および Funder (2008)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-fast)
-   [Gill 他 (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gill)
-   [Golbeck 他 (2011)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-golbeck)
-   [Hirsh および Peterson (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-hirsh)
-   [Yarkoni (2010)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-yarkoni)

こうしたこれまでの研究のほとんどは、書き言葉における言葉の使い方から心理学的に意味のある言葉のカテゴリーを見つけることに基づいています。 このような研究は、{{site.data.keyword.toneanalyzershort}} サービスへの IBM の取り組みの基盤となっています。 心理言語学の研究から得られた科学的研究結果を基に、IBM は人の性格特性、思考と文書のスタイル、感情、内在的な要求、価値観を、その人が書いた言葉から推測しようと取り組んでいます。 IBM は自社の機械学習モデルを使って、人が書いた文書のさまざまな特性を調査し、こうした特性を評価しています。

## 汎用モデル
{: #analysis}

汎用エンドポイントは、用途が広いトーンのセットについて、記述されたコンテンツを分析します。{{site.data.keyword.toneanalyzershort}} サービスは、以下のトーンを含むスコアカードを計算します。

-   **感情トーン**は、IBM の感情分析研究から得られた、テキストから感情を推測するアンサンブル・フレームワークです。 テキストから感情スコアを算出するために、IBM は、スタック汎用化ベースのアンサンブル・フレームワークを使用します。スタック汎用化では、高位モデルを使用して下位モデルをまとめることで予測精度を大きく向上させます。 n-gram (unigram、bigram、trigram)、句読点、顔文字、不快な言葉、あいさつ (例えば「hello」、「hi」、「thanks」)、感情極性などの特性が、感情カテゴリーを分類するための機械学習アルゴリズムに入力されます。
-   **言語トーン**は、学習した特性に基づいて言語分析から計算されます。

### サービスの品質の測定
{: #smqs}

IBM は、前のセクションで述べたトーンのディメンションに沿って、{{site.data.keyword.toneanalyzershort}} サービスの品質を以下のように測定しました。

-   *感情トーン*のカテゴリーのベンチマーク・テストには、ISEAR や SEMEVAL などの標準的な感情データ・セットを使用しました。 その結果、アンサンブル・モデルの平均パフォーマンス (2 つのデータ・セットに対する F1 スコアのマクロ平均は約 41 パーセントと 68 パーセント) は、報告されている最高の精度の最先端モデルのもの (F1 スコアのマクロ平均は約 37 パーセントと 63 パーセント) を統計的に上回っていることが示されました。
-   *言語トーン* は、討論フォーラム、スピーチ、ソーシャル・メディアなどのソースから収集された 20 万を超えるセンテンスを綿密に調査して評価されました。IBM は分析的トーンに 1330 センテンスを、自信トーンとためらいトーンそれぞれに 1000 センテンスをランダムに選択しました。そして、これらのセンテンスを {{site.data.keyword.toneanalyzershort}} サービスに送信すると同時に、人間による分析も依頼しました。

    人による分析では、IBM は [CrowdFlower ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.crowdflower.com/){: new_window} と呼ばれるクラウド・ソーシング・プラットフォームを使用して、選択したセンテンスにさまざまなラベルのアノテーションを付けました。 アノテーション作業への参加は、支持率が 85 パーセントを超える評価者だけに許可しました。 各センテンスに 5 人のアノテーターがラベルを付け、IBM は 5 つのアノテーションの結果の中で最も多く見られるものを使用して、最終ラベルを決定しました。
    -   *分析的トーン*では、人は 1330 センテンスのうち 915 に「分析的である」というラベルを、411 に「分析的でない」というラベルを、4 つに「理解不能」というラベルを付けました。 予測されたラベルをこれらの正解のラベルと比較すると、IBM の分析的トーン検出の F1 スコア は 0.7518 になることがわかりました。
    -   *ためらいトーン*では、人は 1000 センテンスのうち 292 に「ためらっている」というラベルを、706 に「ためらっていない」というラベルを、2 つに「理解不能」というラベルを付けました。 予測されたラベルを正解のラベルと比較すると、IBM のためらいトーン検出の F1 スコアは 0.6369 になることがわかりました。
    -   *自信トーン*では、人は 1000 センテンスのうち 623 に「自信がある」というラベルを、374 に「自信がない」というラベルを、3 つに「理解不能」というラベルを付けました。 予測されたラベルを正解ラベルと比較すると、IBM の自信トーン検出の F1 スコアは 0.7288 になることがわかりました。

全体として、予測されたラベルと正解ラベルの相違は、統計的に有意ではありませんでした。これは、サービスがうまく機能していることを示しています。

## カスタマー・エンゲージメント・モデル
{: #scem}

カスタマー・エンゲージメント・エンドポイントは、カスタマー・ケアの分野のトーンを検出します。 カスタマー・エンゲージメント・モデルで評価するトーンを選択するために、IBM はまず以下の調査を行い、この分野で重要なトーンのディメンションとして受け取られるものを決定しました。

1.  IBM は、マーケティングで使用されるディメンションから 53 トーンのセットを選択し、文書のスタイルを表すために使用するディメンションを選択し、心理学から感情と人格の尺度を選択しました。
1.  IBM は CrowdFlower 上のワーカーに、その 53 のトーン属性がカスタマー・ケアの 1000 の会話に含まれている特定の発話をどの程度表しているかを評価するように依頼しました。 クラウド・ソーシングという環境であるため、評価作業をシンプルにするために、IBM は 53 トーンを 4 つのサブセットに分けました。 人間のアノテーターが評価したのはトーンのサブセットのみです。そして、IBM はそれらの結果の集計から、すべてのトーンの評価を決定しました。
1.  IBM は 53 X 53 の相関行列で因子分析を行い、少なくとも 7 つの有意な因子 (ディメンション) を見つけました。 IBM は、それぞれのディメンションによって表される最も重要な概念を表す因子の名前を決定しました。

このような手順により、カスタマー・ケアの分野の 7 つの重要なトーン・ディメンション、不満、満足、興奮、礼儀正しさ、不作法、悲しみ、共感を決定しました。

### データ収集
{: #sdc}

IBM は、カスタマー・ケア分野のトーン分析のための会話データのソースとして、Twitter のカスタマー・サポート・フォーラムを使用しました。 多くの企業が、顧客にサポートを提供するためのチャネルとして Twitter を使用しています。 自社に言及するツイートをモニターすること、支援要求を振り分けること、顧客のニーズに対応するための迅速なサポートを提供することを目的に、担当者が雇用されてトレーニングを受けています。

できる限り多くの会話を収集するために、IBM は Twitter 上にカスタマー・サービス専用のアカウントを持つ 62 のブランドを選択しました。 IBM は、さまざまな業種、地理的位置、組織規模をカバーできるようにそれらのブランドを選択しました。 全体として、IBM は、2016 年 6 月 1 日から 8 月 1 日までの間に、260 万のユーザー要求を収集しました。

### データ・アノテーション
{: #sda}

IBM は収集したデータ・セットを選別し、1 人の顧客と 1 人の担当者だけによる会話で、返事が 1 つ以上あるものを残しました。 また、IBM は、英語以外の会話と、画像を含む要求や回答がある会話はすべてデータ・セットから削除しました。 ユーザーと企業のプライバシーを保護するために、IBM は、すべての会話の中のすべての *@mentions* を、*@customer*、*@[industry]_company* (例えば、*@ecommerce_company* や *@telecommunication_company*)、*@competitor_company*、または *@other_users* に置き換えました。

この選別プロセスにより、CrowdFlower のワーカーにアノテーションを付けてもらう約 96,000 の会話発話が決まりました。 アノテーションのコンテキストについての理解を深めるために、IBM は、会話レベルでアノテーションを付け、会話に含まれているすべての発話にラベルを付けるようにワーカーに依頼しました。 提示したトーンの中には、そもそも受け取られ方が一貫しないものもありました。そこで IBM は、発話がトーンを示していると感じる強さの程度を、「非常に強く感じる」から「まったく感じない」までの範囲の 4 ポイントのリッカート尺度で表すようにアノテーターに依頼しました。リッカート尺度は、さまざまな感じ方に対する許容度が高く、ラベルの数が多いので、2 値の単純な yes/no の尺度よりも望ましい尺度です。

5 人の異なるアノテーターが各会話にラベルを付けました。 IBM は、前のアノテーション作業で許容レベルの貢献をしてくれた米国在住のアノテーターのみを採用しました。 また、トレーニング用の 5 つの質問に正しく答えたアノテーターのみが実際のアノテーション作業を始められることにしました。 トレーニング用の質問により、各トーンがカスタマー・サービスのコンテキストで何を意味するのかをアノテーターが理解できるようにしました。 また、IBM は、アノテーターのラベルの品質をさらに検証するために、実際の作業に検証の質問を組み込みました。

IBM は、各発話の最終ラベルとして、5 人のアノテーターのスコアの平均を使用しました。 そして、ラベルを 2 値に変換するためのしきい値として、スコア 1 を使用しました。 1 をしきい値として選択した根拠は、ラベル分布の観察と、しきい値が異なる複数のモデルの性能を基にしています。 最終的な結果としては、不満が 9536、満足が 10,806、興奮が 6107、礼儀正しさが 63,853、不作法が 1688、悲しみが 24,954、共感が 10,475 という発話の分布になりました。

### トーンの学習モデル
{: #sltm}

このカスタマー・エンゲージメント会話に基づき、IBM はサポート・ベクター・マシン (SVM) をベースにした機械学習モデルをトレーニングして、カスタマー・ケアの新しい発話のトーンを予測しました。 機械学習モデルで、IBM は以下のようないくつかのカテゴリーの特性を活用しました。

-   N-gram 特性
-   各種辞書の字句の特性
-   会話での二人称表現の存在
-   感謝や謝罪などの対話固有の特性
-   疑問符や感嘆符の連続出現などの、いくつかのより高度な特性

サンプルの約 30 パーセントが複数のトーンを含むことが明らかになりました。 そのため、IBM は多クラス分類作業ではなく、多ラベル分類作業を解決することを選択しました。トーンごとに、IBM は One-vs-Rest (OVR) パラダイムを使用して単独でモデルをトレーニングしました。 このパラダイムでは、各クラスの発話をポジティブ・サンプルとして使用し、他のすべての発話をネガティブ・サンプルとして使用しました。 IBM は、少なくとも 2 分の 1 の確率で予測されたトーンを最終トーンと見なしました。いくつかのトーンでは、トレーニング・データはかなりアンバランスでした。そのため IBM は、トレーニング時に各トーンのコスト関数の最適な重み値を特定しました。

IBM は、精度、再現率、F スコアを使用して、自社の分類モデルの正確度を評価しました。 モデルは、ベンチマーク・データ・セットと比べて、高い正確度を示しました。
