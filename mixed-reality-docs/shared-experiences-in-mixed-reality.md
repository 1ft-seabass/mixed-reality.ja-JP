---
title: 複合現実での経験を共有
description: Holographic アプリは、HoloLens の 1 つから現実の世界で同じ場所でホログラムを複数のデバイスで表示するためにユーザーを有効にすると、別の空間のアンカーを共有することができます。
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 混合、実際には、ホログラム、空間アンカー、マルチ ユーザー マルチ共有のエクスペリエンス
ms.openlocfilehash: b27da1e73c927a26e33746cd2db08e67c6f70acc
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605131"
---
# <a name="shared-experiences-in-mixed-reality"></a>複合現実での経験を共有

ホログラムは、常に 1 つだけのユーザーに対してプライベートである必要はありません。 Holographic アプリ共有[空間アンカー](coordinate-systems.md)から、HoloLens、iOS または Android のデバイス間を 1 つにするには、複数のデバイスで実際に同じ場所でホログラムを表示するためにユーザーを有効にします。

## <a name="six-questions-to-define-shared-scenarios"></a>共有のシナリオを定義する 6 つの質問

共有エクスペリエンスの設計を開始する前に、対象となるシナリオを定義する必要があります。 これらのシナリオを明確にして設計を確認し、確立に役立つ一般的な用語を比較し、お客様のエクスペリエンスで必要な機能を比較します。 詳細については、主要な問題とソリューションの別の手段は、営業案件のこの新しいメディアに本質的な明らかにキーです。

内部プロトタイプと、HoloLens パートナー会社からの探索では、共有のシナリオを定義するために 6 つの質問を作成しました。 これらの質問は、自分のシナリオの重要な属性を抽出するため、すべてを網羅するものでありません、フレームワークを形成します。

### <a name="1-how-are-they-sharing"></a>1. 方法を共有するでしょうか。

共同作業を行う複数のユーザー、または、教師は仮想マテリアルを使用する仮想の受講者にガイダンスを提供する可能性があります、1 つの仮想ユーザーがプレゼンテーションを誘導可能性があります: ユーザーが会社のレベルに基づいて、エクスペリエンスが増加の複雑さやシナリオで持つことができます。

![男性と女性 holograph テーブルでの](images/man-and-women-with-holograph-on-table-500px.png)

を共有する方法はたくさんありますが、これらのほとんどが 3 つのカテゴリに分類ことがわかりました。
* **プレゼンテーション**:ときに、同じコンテンツがいくつかのユーザーに表示されます。 例:教授は、すべてのユーザーに表示されている同じ holographic 素材を使用しているいくつかの学生に講義を与えています。 教授、ただしことができます独自のヒントと他のユーザーに表示されることができない可能性があるノートが記載します。
* **コラボレーション**:ときにユーザーがいくつかの一般的な目標を達成するためにまとめて作業します。 例:ハート手術を実行する詳細については、プロジェクトをした教授です。 学生を組み合わせるし、中心モデルで共同作業し、学習するには、医療受講者をできる共有スキル ラボ エクスペリエンスを作成します。
* **ガイダンス**:1 人のユーザーより 1 つの問題を解決するためにユーザーが、支援と相互作用のスタイルを設定します。 例:教授がハート手術スキルのラボを実行する共有のエクスペリエンスでは、自分がときに学生へのガイダンスを提供します。

### <a name="2-what-is-the-group-size"></a>2. グループのサイズとは何ですか。

**一対一**強力なベースラインを提供することができますの経験を共有し、概念実証を作成して、このレベルが理想的です。 こと (6 人) を超える大規模なグループと共有につながる問題がある場合 (データおよびネットワーク) のテクニカルから社会に注意してください (室に配置されるの影響[いくつかのアバター](https://vimeo.com/160704056))。 すぐに複雑さが指数関数的に増加**小さな**に**大きなグループ**します。

グループのニーズがサイズの 3 つのカテゴリに分類できることがわかりました。
* 1:1
* 小さな < 7
* 大規模な > = 7

グループのサイズに与える影響があるために、重要な質問の。
* Holographic 領域内のユーザーの表現
* オブジェクトの小数点以下桁数
* 環境のスケール

### <a name="3-where-is-everyone"></a>3.すべてのユーザーとは?

複合現実の強度では、共有のエクスペリエンスを同じ場所に実行できる場合が登場します。 呼び出して**併置**します。 逆に、グループの配布を少なくとも 1 つの参加者が同じ物理領域 (VR の場合は、多くの場合)、時に呼び出してをリモート エクスペリエンス。 多くの場合、グループがある場合は**両方**併置とリモートの参加者 (会議室での 2 つグループなど)。

![テーブルで holograph で 3 人のユーザー](images/three-people-with-holograph-on-table-500px.png)

次のカテゴリは、ユーザーがいる場所を伝えるのに役立ちます。
* 併置されています。すべてのユーザーは、同じ物理領域になります。
* リモート。すべてのユーザーは、別の物理的なスペースになります。
* 両方とも：ユーザーは、併置されていると、リモートの空白文字の組み合わせになります。

いくつかの理由はなぜこの質問がきわめて重要ですが影響を与えます。
* ユーザーが通信する方法でしょうか。
* 次に、例を示します。かどうか、アバターが必要ですか。
* オブジェクトが表示されます。 すべてのオブジェクトが共有されますか。
* かどうか、環境に適応する必要がありますか。

### <a name="4-when-are-they-sharing"></a>4。ときに、共有しますか。

一般的**同期**共有エクスペリエンスが頭に浮かぶときに発生します。すべてを行っていますがまとめて。 他のユーザーによって追加された 1 つの仮想要素が含まれていて、必要がある、**非同期**シナリオ。 注、または音声メモ、仮想環境で左を想像してください。 100 の仮想メモ、設計上の残りの処理方法 場合は多くの人々 からさまざまなレベルのプライバシーのでしょうか。

これらのカテゴリの時間の 1 つとして、お客様のエクスペリエンスを検討してください。
* **同期的に**:同時にホログラフィック操作を共有します。 例:2 つの受講者が同時に、スキルのラボを実行します。
* **非同期的に**:さまざまなタイミングで holographic のエクスペリエンスを共有します。 次に、例を示します。2 つの学生スキル ラボを実行するが、異なる時刻で個別のセクションで作業します。
* **どちらも**:ユーザーも共有するには同期的に他の時間が非同期的に。 例:次の日の後で受講者のノートをしたまま、受講者によって実行割り当て成績評価教授です。

この質問が重要な理由に与える影響のため、いくつかの理由:
* オブジェクトと環境の永続化します。 次に、例を示します。取得できるように、状態を保存します。
* ユーザーのパースペクティブです。 例:どのようなユーザーが求めていたでノートの終了時におそらく記憶します。

### <a name="5-how-similar-are-their-physical-environments"></a>5。類似性には、物理環境か。

併置のエクスペリエンスの外部で同一の実際の環境は 2 つの確率値は、これらの環境が同一であるように設計されている場合を除き、slim です。 させる可能性が高く**のような**環境。 たとえば、会議室は似ています — 通常椅子で囲まれた一元的に配置されているテーブルがあります。 リビング ルームはその一方で、通常は**異種**レイアウトの無限配列の任意の数の家具の情報を含めることができます。

![テーブルで holograph](images/holograph-on-table-500px.png)

これら 2 つのカテゴリのいずれかに合った、共有のエクスペリエンスを検討してください。
* **ような**:ような家具、周辺光とサウンド、存在する傾向がある環境の物理的スペースのサイズ。 次に、例を示します。教授が講義 hall A では、受講者講義 hall B. 講義 hall A が B よりも少ない椅子を必要がありますが、どちらも、物理のデスクにホログラムを配置する場合があります。
* **複数の異なる**:家具設定、部屋のサイズ、光とサウンドに関する考慮事項の非常に異なっている環境。 例:教授は、学生が学生と教員塗りつぶす大きな講義 hall では、フォーカス部屋には。

影響を及ぼします環境について考慮する必要があります。
* ユーザーはこれらのオブジェクトをどのようにが発生します。 次に、例を示します。お客様のエクスペリエンスは、テーブルと、ユーザーに最も適している場合に、テーブルがないでしょうか。 または、フラット床面が、ユーザーが乱雑にならない領域。
* オブジェクトの小数点以下桁数。 次に、例を示します。難しい可能性があるテーブルの 6 フィート人間のモデルを配置することが中心モデルはうまく機能します。

### <a name="6-what-devices-are-they-using"></a>6。どのようなデバイスを使用しているでしょうか。

今すぐする多くの場合、2 つの共有エクスペリエンスが表示される可能性**没入型デバイス**(ボタンと相対的な能力の観点から、それらのデバイスが若干異なる場合がありますが大幅にしない) または 2 つ**holographic デバイス**これらのデバイスを対象となるソリューションを指定します。 ものだと考えますが、 **2D デバイス**(モバイル/デスクトップ参加者またはオブザーバー) に特にの状況での必要な考慮事項をする**2D および 3D のデバイスを混合**します。 参加者を使用してデバイスの種類については、ユーザーが各プラットフォーム用の一意の期待がさまざまな忠実性とデータの制約と営業案件、付属のためだけでなく、重要です。

## <a name="exploring-the-potential-of-shared-experiences"></a>共有エクスペリエンスの可能性の調査

エクスペリエンスを展開する際の課題を crystallizing、共有のシナリオを理解するのには、上記の質問に対する回答を結合できます。 マイクロソフトのチーム、これにより、エクスペリエンスを向上させるためのロードマップを確立使用今日、複合現実での共有エクスペリエンスを利用する方法とこれらの複雑な問題の微妙な違いを理解します。

たとえば、HoloLens の起動からの Skype のシナリオのいずれかを検討してください: ユーザーに対処[破損したライトのスイッチを修復する方法](https://www.youtube.com/watch?v=iBfzs3G8BEA)リモートにある専門家の支援によりします。

![HoloLens の Skype によるアシスタンスでのライトのスイッチの修正](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>エキスパートが提供<b>1:1</b>彼からガイダンス<b>2D</b>、デスクトップ コンピューターのユーザーに、 <b>3D、複合現実</b>デバイス。<b>ガイダンス</b>は<b>同期</b>物理環境と<b>異種</b>します。</i>

このようなエクスペリエンスは現在の経験からの手順-変更-新しいメディアにビデオと音声のパラダイムを適用します。 将来的に見られるようにする必要がありますよりシナリオの営業案件の定義し、複合現実の強度を反映するためのエクスペリエンスを構築します。

検討してください、 [OnSight コラボレーション ツール](https://www.youtube.com/watch?v=ZOWQp0-Bkkw)NASA のジェット推進研究所によって開発されました。 Mars rover ミッションのデータ科学者が内の同僚と共同作業を行う Martian 横から、データ内でリアルタイムです。

![Mars Rover の作業を計画にリモートで区切られた同僚の間の共同作業](images/onsight-nasa-jpl.gif)

<i>科学者は、環境を使用して、について説明します、 <b>3D、複合現実</b>でデバイスを<b>小さな</b>グループの<b>リモート</b>を使用して同僚<b>3D および 2D</b>デバイス。<b>コラボレーション</b>は<b>同期</b>(ただし、非同期的に再考できます)、(実際) は物理環境と<b>のような</b>します。</i>

OnSight などのエクスペリエンスは、共同作業を行う新しい機会を提示します。 物理的に立って、仕事仲間の横にあると、調査結果について説明しますが、パースペクティブを共有する仮想環境での要素を指しています。 OnSight は、immersion とプレゼンスのレンズを使用して複合現実での共有エクスペリエンスを再考します。

直感的なコラボレーションは、メッセージ交換および連携の基盤と複合現実の複雑さをこの直感を適用する方法を理解することが重要です。 複合現実での共有エクスペリエンスを作成し直すことだけでなく、それらのパワーアップする場合、は、作業の将来のパラダイム シフトをことができます。 複合現実での共有エクスペリエンスの設計は、新しいとおすすめの機能領域、私たちは、先頭にのみです。

## <a name="get-started-sharing-experiences"></a>体験の共有を開始します。

アプリケーションとシナリオに応じて、必要なエクスペリエンスを実現するためにさまざまな要件があります。 これらのもの
* 一致します。セッションを作成、セッションを提供し、発見、特定の両方でローカルのユーザーを招待し、リモート セッションに参加する機能。
* 共有を固定するには。ホログラムがすべてのユーザーに対して同じ場所に表示されるように、複数のデバイスで共通のローカル空間で座標を調整することです。
* ネットワーク:する機能を置くと、相互作用とでのユーザーとホログラムの動きが同期されているすべての参加要素はリアルタイムです。
* 状態の記憶域:セッション中に結合のスペースでホログラム特性と場所を格納するのには、取り消し後の時刻、およびネットワークの問題に対する堅牢性に機能します。


共有エクスペリエンスにキーは、複数のユーザーが自分のデバイスはデバイス間で座標に合わせてアンカーを共有することでよく行われますが、世界中で同じホログラムを表示します。
アンカーを共有するには、使用、 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>:
* まず、ユーザーは、ホログラムを配置します。
* アプリを作成、[空間アンカー](coordinate-systems.md)世界中で正確には、そのホログラムをピン留めします。
* HoloLens、iOS および Android デバイスを使用してアンカーで共有できることができます、 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>します。 

共有の空間アンカーを持つ各デバイスでアプリはコンテンツを配置する一般的な座標系ようになりましたが。 今すぐアプリを配置し、同じ場所にあるホログラムの向きを設定する保証できます。
HoloLens デバイスで、アンカー オフライン 1 つのデバイスから間を共有することもできます。  以下のリンクを使用して、アプリケーションに最適なものを決定します。


## <a name="see-also"></a>関連項目
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure の空間アンカー</a>
* [DirectX のアンカー空間の共有](shared-spatial-anchors-in-directx.md)
* [Unity での共有エクスペリエンス](shared-experiences-in-unity.md)
* [Spectator ビュー](spectator-view.md)