---
title: Holographic フレーム
description: ユーザーは、holographic、フレームを使って複合現実の世界を参照してください。
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: フレーム、HoloLens、Windows Mixed Reality、ホログラフィック ビューのフィールド
ms.openlocfilehash: 6773bc03dea471c97d0c6006d2ab7853a5ef3669
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598791"
---
# <a name="holographic-frame"></a>Holographic フレーム

ユーザーには、ヘッドセットを搭載した四角形のビューポートを複合現実の世界を参照してください。 HoloLens は、この四角形領域は、holographic のフレームは呼び出され、デジタル コンテンツの周囲に現実の世界にオーバーレイを表示することができます。 Holographic フレーム用に最適化されたエクスペリエンスを設計機会、課題の軽減、複合現実のアプリケーションのユーザー エクスペリエンスを向上します。

## <a name="designing-for-content"></a>コンテンツのための設計

多くの場合、デザイナーと何がすぐに表示するエクスペリエンスのスコープを制限する必要が、オブジェクト全体でユーザーに実際のスケールを犠牲にすることが表示されます。 同様に複雑なアプリケーションを持つデザイナー多くの場合、オーバー ロードのコンテンツを含む、holographic フレーム困難な相互作用と乱雑インターフェイスを持つユーザーを過負荷。 デザイナーの複合現実のコンテンツを作成する必要がありますがエクスペリエンスに直接も、ユーザーとの即時ビュー内で制限はありません。 物理世界のユーザーがマップされている場合、これらすべてのサーフェスを考慮デジタル コンテンツとの相互作用の潜在的なキャンバスします。 相互作用とエクスペリエンスを内のコンテンツの適切な設計では、キーのコンテンツに関心を指示する、および複合現実の完全な可能性を参照してください。 支援は空き領域を移動するユーザーを促す必要があります。

期待の持てるものの移動と、アプリ内で探索する最も重要な手法が、おそらく**ユーザー エクスペリエンスを調整できるように**します。 デバイスには、' タスク フリー ' の期間の短いユーザーを提供します。 これは、空間内のオブジェクトの配置、ユーザーがその周囲に移動できるようにすることやナレーション、エクスペリエンスの概要として簡単なことができます。 この時間が、重要なタスクの無料、代わりにユーザーの対話機能を必要とするか、アプリの段階で進行して前に、デバイスからコンテンツを表示するに対応できるようにする目的のエア タップすると)、(など、特定がジェスチャで必要です。 これが、デバイスとユーザーの初めての場合は、holographic のフレームとホログラムの性質を使いやすい表示コンテンツを取得する際に特に重要です。

### <a name="large-objects"></a>ラージ オブジェクト

多くの場合、コンテンツのためには、エクスペリエンス、特に実際のコンテンツはより大きくする holographic のフレーム。 (より小さいスケールまたは距離で) 最初に導入された場合に合わせて holographic の枠内に収まらない通常オブジェクトを圧縮する必要があります。 重要**ユーザー オブジェクトの完全なサイズを表示できるように**前に、小数点以下桁数は、フレームをあまり使わなくなります。 フォームのサイズを変更する前に、対象の動物の全体的な図形の空間を理解できるように、フレームを完全に収まるようの holographic 象の表示など、[実際のスケール](scale.md)ユーザーの近くです。

考慮して、オブジェクトの完全なサイズ、ユーザーを移動し、そのオブジェクトの特定の部分の検索場所のことを期待し、あります。 同様に、没入型のコンテンツの使用経験、そのコンテンツの最大サイズを参照する方法を用意するために役立つ、ことができます。 たとえば、仮想の家のモデルを歩き、エクスペリエンスが含まれている場合にユーザーをトリガーできますが、家の内部を理解するエクスペリエンスの小さい人形家サイズ バージョンが含ま役立ちます。

ラージ オブジェクトの設計の例は、次を参照してください。 [Volvo 自動車](holographic-frame.md#volvo-cars)します。

### <a name="many-objects"></a>多くのオブジェクト

多くのオブジェクトまたはコンポーネントと共にエクスペリエンスでは、ユーザーを直接売り込む holographic のフレームの混乱を避けるため、ユーザーの周りの完全なスペースを使用して検討してください。 一般に、緩やかに変化を経験するコンテンツを導入することをお勧めし、これは、ユーザーに多くのオブジェクトを処理するために計画したエクスペリエンスを特に当てはまります。 キーが、大きなオブジェクトで同様に**ユーザーがコンテンツのレイアウトを把握できるように**エクスペリエンスでは、それらのコンテンツが、エクスペリエンスに追加される周囲に新機能の空間的に理解を支援します。

これを実現する 1 つの方法では、現実の世界にアンカー コンテンツ エクスペリエンスで永続的なポイント (ランドマークとも呼ばれます) を提供します。 たとえば、ランドマークでは、物理オブジェクトでは、実際のデジタル コンテンツが表示されるテーブルまたは一連のコンテンツが頻繁に表示されるデジタル画面などのデジタル オブジェクトなどの可能性があります。 オブジェクトは、ユーザーによって、周辺以外のコンテンツの検出を支援できます中に、コンテンツ、キーに向かって検索をお勧めします holographic 枠の周囲に配置することも[注意取締役](holographic-frame.md#attention-directors)します。

側に検索するユーザーに促すことができます、周辺のオブジェクトを配置して、この以下に示すよう注意の取締役で支援することができます。

## <a name="user-comfort"></a>快適性

ラージ オブジェクトまたはオブジェクトの多くで、複合現実エクスペリエンスの head 量を考慮することが重要と首部分移動コンテンツと対話する必要があります。 エクスペリエンスは、ヘッドの移動の観点から 3 つのカテゴリに分類できます。**水平**(左右)、**垂直**(上下)、または**没入型**(水平方向および垂直方向)。 可能であれば、理想的には行わ holographic のフレームの中央にユーザーの頭がニュートラル位置の間ほとんどのエクスペリエンスと水平方向または垂直方向のいずれかのカテゴリの対話処理の大部分を制限します。 原因で継続的に、ビューを (たとえば、アクセス キー] メニューの [相互作用を常に検索) の不自然なヘッド位置に移動するユーザーの相互作用を回避します。

![コンテンツの最適な領域が 0 ~ 35 ° 水平線の下](images/optimal-field-of-view-2-750px.png)<br>
*コンテンツの最適な領域が 0 ~ 35 ° 水平線の下*

水平ヘッドの移動は[快適](comfort.md)一般的でないイベントの垂直方向の動きを予約するときに、頻繁にやり取りします。 たとえば、長い水平のタイムラインに関連する経験は、(メニューにある見下ろした) などの相互作用の垂直ヘッドの移動を制限する必要があります。

ユーザーの領域の周囲のオブジェクトを配置することによってだけヘッドの移動ではなく、全本文の移動を促進することを検討してください。 オブジェクトまたは大きなオブジェクトの移動にエクスペリエンスでは、ヘッドの移動、特に必要がある水平および垂直方向の両方の軸に沿った頻繁に移動する特別な注意を払う必要があります。

## <a name="interaction-considerations"></a>相互作用に関する考慮事項

コンテンツと同様、複合現実エクスペリエンスでの相互作用必要はありません、ユーザーことがすぐに表示される内容に制限されています。 相互作用を実行できる任意の場所で、ユーザーの周りの実際のスペースとユーザーを移動し、エクスペリエンスの詳細をお勧めします。 これらのインタラクションが役立ちます。

### <a name="attention-directors"></a>注意ディレクター

関心の高いキー相互作用を示すポイントはエクスペリエンスを通じてユーザーが進行するために重要にできます。 ユーザーの注意と holographic のフレームの移動は、軽度または過酷な方法で送信できます。 ユーザーの混乱を回避 (特に、エクスペリエンスの開始) に複合現実での無料の探索の期間を含む注意取締役のバランスを取るに注意してください。 一般に、これには注意取締役会の 2 つの種類があります。
* **ビジュアルの責任者:** ユーザーに特定の方向に移動する必要がありますを通知する最も簡単な方法を視覚を提供することです。 これ行う視覚効果 (たとえば、ユーザー エクスペリエンスの次の部分に向けたに従って視覚的にパス)、またはも単純な方向矢印として。 すべての視覚インジケーターが必要がある注意は、'に接続されていない ' holographic フレームまたはカーソルのユーザーの環境内で接地します。
* **オーディオの責任者:**[空間サウンド](spatial-sound-design.md)(エクスペリエンスに入るオブジェクトのユーザーに警告する) シーン内のオブジェクトを確立するために、または (キー オブジェクトへのユーザーのビューに移動) する空間内の特定の点に注意してくださいに出力するための強力な方法を提供できます。 オーディオのディレクターを使用してユーザーの注意をガイドするより微妙で visual 取締役よりもさほどがあります。 場合によっては、オーディオ ディレクターでは、使用を開始から、ユーザーは、キューを認識しない場合は、visual director 移動することをおができます。 オーディオの責任者は、追加の強調のためのビジュアルの取締役でも対応できます。

### <a name="commanding-navigation-and-menus"></a>コマンドの実行、ナビゲーション、およびメニュー

理想的には複合現実エクスペリエンスのインターフェイスは、制御しているデジタル コンテンツと緊密にペアは。 そのため、フローティング状態である 2D メニューでは、相互作用に最適では多くの場合と、快適で holographic フレーム内のユーザーには困難が伴います。 メニューまたはテキスト フィールドなどのインターフェイス要素を必要とエクスペリエンスを使用して検討してください、 [tag-along メソッド](billboarding-and-tag-along.md)しばらく holographic のフレームに従う。 これは、ユーザーと中断ことで、シーン内の他のデジタル オブジェクト臨場感の迷子できるように、フレーム、ヘッドアップ ディスプレイのようにコンテンツをロックしないでください。

または、検討直接特定のインターフェイス要素を配置するコンテンツ コントロールをユーザーの物理的なスペースを自然に発生する相互作用を許可します。 たとえば、複雑なメニューを別々 の部分に分割します。 各ボタンとコントロールのグループの操作に影響する特定のオブジェクトにアタッチされます。 この概念をさらに実行するには、使用を検討[対話型のオブジェクト](interactable-object.md)します。

### <a name="gaze-and-gaze-targeting"></a>視線入力し、視線の先を対象とします。

Holographic のフレームでは、開発者はトリガーの相互作用について説明するツールだけでなく、ユーザーの注意 dwells を評価します。 [視線](gaze.md)の 1 つです、 [HoloLens の相互作用をキー](interaction-fundamentals.md)視線の先は組み合わせることができますが、[ジェスチャ](gestures.md)(などのエア タップ) または[音声](voice-input.md)(許可の短い、より自然な音声ベースの相互作用)。 そのため、これにより、holographic のフレームが両方とやり取りすることと、デジタル コンテンツを観察する場所。 場合は、エクスペリエンスを呼び出すと、ユーザーの領域 (注視 + ジェスチャでユーザーの領域を複数選択することオブジェクトなど) を基準として複数のオブジェクトと対話するため、ユーザーのビューにこれらのオブジェクトを移動または必要に応じて頭の量を制限を検討してください。昇格する移動[快適性](comfort.md)します。

視線の先を使用してエクスペリエンスを通じてユーザーの注意を追跡してオブジェクトを確認することもできます。 またはユーザーのシーンの部分は有料にほとんど注意します。 ヒートマップをユーザーが最大限に費やしている場所を確認または特定のオブジェクトまたは相互作用がないような分析ツールの許可、エクスペリエンスのデバッグに使用では特にこのことができます。 追跡視線の先が推進エクスペリエンスでの強力なツールも提供できます (を参照してください、 [Lowe の台所](holographic-frame.md#lowes-kitchen)例)。

## <a name="performance"></a>パフォーマンス

Holographic のフレームの適切な使用は、基本となる、[パフォーマンス品質](understanding-performance-for-mixed-reality.md)で発生します。 テクニカル (と使いやすさ) の一般的な課題には、ユーザーのフレームのレンダリング パフォーマンスが低下する原因と、デジタル コンテンツにはオーバー ロードします。 検討してください、ユーザーの周りの完全なスペースを使用してデジタル コンテンツを配置する代わりに、手法を使用して、上記のレンダリングの負担を軽減し、最適な表示品質を保証します。

HoloLens の holographic の枠内でのデジタル コンテンツを組み合わせてもできる、[安定化平面](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)最適なパフォーマンスと[ホログラム安定性](hologram-stability.md)。

## <a name="examples"></a>例

### <a name="volvo-cars"></a>Volvo 自動車

>[!VIDEO https://www.youtube.com/embed/DilzwF90vec]

Volvo 車から showroom エクスペリエンス、お客様を招待して Volvo 関連付けによって実行される HoloLens の経験では新しい自動車の機能について説明します。 Volvo 問題に直面 holographic のフレームを: フルサイズの車が大きすぎて、ユーザーの横にある右に配置します。 ソリューションは、物理ランドマーク、中心となるテーブル、テーブルの上に配置する車の小さなデジタル モデルで、showroom 経験を開始するでした。 これにより、ユーザーが表示される完全な自動車が導入されると、車のエクスペリエンスの後で、実際のスケールを拡大すると、空間についての理解することができます。

Volvo のエクスペリエンスはでも show 室の壁にテーブルの小規模な自動車のモデルから時間の長い視覚効果を作成、ビジュアルの取締役会を使用します。 これは、距離にある自動車の完全なビューを表示、現実世界規模での自動車のさらに機能を示す、'マジック ウィンドウ' 効果につながります。 ヘッドの移動は、(視覚的にし、エクスペリエンスの Volvo の担当者のナレーションの代わりにキューを収集する)、ユーザーからは直接やり取りせず、水平方向です。

### <a name="lowes-kitchen"></a>Lowe の台所

Lowe からのストアのエクスペリエンスは、運用時並みのモックアップ キッチン、HoloLens で表示される、さまざまなリフォーム機会を紹介するのにお客様を招待します。 ストアにキッチンでは、デジタル オブジェクトの物理的背景、アプライアンス、countertops、および展開する複合現実エクスペリエンスのキャビネットの空白のキャンバスを提供します。

物理サーフェスは、Lowe の関連付けがさまざまな製品オプションおよびが完了すると、ユーザーをガイドとして、ユーザー エクスペリエンスでは、地上自体が静的のランドマークとして機能します。 この方法で、関連付けは、'冷蔵庫' または 'ショーケース デジタル コンテンツに ' キッチンの中央にユーザーの注意を直接口頭で送信できます。

![Lowe の関連付けは、タブレット、HoloLens エクスペリエンスを通じて顧客をガイドを使用します。](images/loweskitchen-750px.jpg)<br>
*Lowe の関連付けは、タブレット、HoloLens エクスペリエンスを通じて顧客をガイドを使用します。*

ユーザーのエクスペリエンスは、Lowe の関連付けによって制御されるタブレット エクスペリエンスによって管理されますの一部が。 担当者の役割の一部は、この場合、キッチンで関心のあるポイント間で、注意をスムーズに転送すること、過剰なヘッドの移動を制限する場合にも。 タブレットのエクスペリエンスには、ユーザーが (たとえば、キャビネットの特定の領域) にもたらすによりガイダンスをより正確に提供を理解していただくため、キッチンのヒートマップ ビューの形式でデータを注視 Lowe の関連付けも用意されています。

Lowe の台所エクスペリエンスの詳細については、次を参照してください。 [Ignite 2016 の Microsoft の基調講演](https://www.youtube.com/watch?v=gC_4JxF0e_k)します。

### <a name="fragments"></a>フラグメント

HoloLens のゲーム フラグメントでは、リビング ルームが仮想犯罪現場の手がかりと証拠、さらに、椅子に座って、壁に依存する文字の場所と通信する、仮想会議室の表示に変換されます。

![フラグメントは、現実世界のオブジェクトおよびサーフェスと対話する文字を含むユーザーのホームで実行するように設計されました。](images/fragments-750px.jpg)<br>
*フラグメントは、現実世界のオブジェクトおよびサーフェスと対話する文字を含むユーザーのホームで実行するように設計されました。*

ユーザーが最初に、エクスペリエンスを開始するときは短期間の調整、ごくわずかな相互作用が必要な場合、特定の代わりに促すことを見回してください。 これは、ルームがゲームの対話型コンテンツを正しくマップされてことを確認にも役立ちます。

エクスペリエンス全体で文字が焦点になります、visual ディレクター (ヘッドの移動を探すか、関心のある領域に向けたジェスチャにすると、文字間) として機能します。 ゲームはまたユーザー オブジェクトまたはイベントを検索する時間がかかるが、視覚的手掛かりをより目立たに依存し、(特にシーンを入力するときに、音声を文字) と空間的なオーディオを多用します。

### <a name="destination-mars"></a>送信先: Mars

コピー先。Mars のエクスペリエンスの機能を備えた[NASA の Kennedy 領域 Center](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)Mars、伝説飛行士 Buzz Aldrin の仮想表現でのガイド付きの画面に没入型の旅行に招待された訪問者。

![仮想の Buzz Aldrin では、先にユーザーの起点になります。Mars します。](images/destinationmars-750px.png)<br>
*仮想の Buzz Aldrin では、先にユーザーの起点になります。Mars します。*

魅力的なエクスペリエンスとしてこれらのユーザー仮想 Martian ランドス ケープを表示するすべての方向に自分の頭を移動周りを推奨されました。 ユーザーの快適性を確実が Buzz Aldrin のナレーションと仮想のプレゼンス エクスペリエンスのあらゆる場所の中心点が用意されています。 この仮想の記録と (によって作成された[Microsoft の混合実際のキャプチャ Studios](https://www.microsoft.com/mixed-reality/capture-studios)) ほぼ完全なビューを参照してください (英語) できるように、部屋の隅にある、real、人間のサイズで縦です。 評判のナレーションに環境内でさまざまな地点に集中するユーザーが送られます (たとえば、フロアまたは距離で mountain 範囲火星のセット rocks) された特定のシーンの変更または自分がで導入されたオブジェクト。

![仮想頼って、エクスペリエンス全体で強力な中心点を作成する次のユーザーの移動になります。](images/gazereset-750px.png)<br>
*仮想頼って、エクスペリエンス全体で強力な中心点を作成する次のユーザーの移動になります。*

評判の現実的な表現では、講演する彼は、あると解釈するユーザーに向けたの評判を有効にする微妙な手法を備えた強力な中心点が用意されています。 エクスペリエンスについて、ユーザーが移動すると評判がシフト手前にしきい値に彼の周囲を超えるユーザーが離れすぎてが移動する場合に、ニュートラルな状態に戻る前に。 評判から完全に (たとえば、シーンの他の場所で何かを確認する) の方法を表示する場合、ナレーターの方向の位置は 1 回の評判に戻りますもう一度に注目がユーザー。 このような手法が immersion の強力な意味を指定し、過剰なヘッドの移動を削減し、昇格の holographic のフレーム内の中心点を作成[快適性](comfort.md)します。

## <a name="see-also"></a>関連項目
* [相互作用の基礎](interaction-fundamentals.md)
* [快適性](comfort.md)
* [スケール](scale.md)
* [視線の先を対象とします。](gaze-targeting.md)
* [ホログラム安定性](hologram-stability.md)