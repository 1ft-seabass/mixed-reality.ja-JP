---
title: ジェスチャ
description: 手のジェスチャでは、複合現実でアクションを実行するようにします。
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: 複合現実、ジェスチャ、相互作用、設計
ms.openlocfilehash: afebefddfd620b4697b86616e8ecc930b271dca2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597564"
---
# <a name="gestures"></a>ジェスチャ

手のジェスチャは、複合現実でのユーザー アクションの実行を許可します。 相互作用が上に構築された**視線**をターゲットと**ジェスチャ**または**音声**にどのような要素が対象となって動作します。 手のジェスチャでは、空間における正確な場所は提供しませんが、HoloLens に配置して、すぐにコンテンツを操作するがわかりやすくするためには、[アクセサリ]、せずに作業を取得するユーザーができるようにします。

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> ジェスチャ</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
<tr>
<td> 関節手</td><td></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。

## <a name="gaze-and-commit"></a>視線の先コミット

アクションを実行し、手のジェスチャの使用を[ヘッド注視](gaze.md)ターゲット メカニズムとして。 組み合わせ**視線**と**エア タップ**ジェスチャで結果を**視線の先コミット**相互作用します。 視線の先にコミットする代わりに**ポイント-コミット**によって有効になっている、[コント ローラーのモーション](motion-controllers.md)します。 HoloLens で実行されるアプリのみ、HoloLens でモーションのコント ローラーがサポートされていないために、視線の先にコミットをサポートする必要があります。 HoloLens、イマーシブ ヘッドセットの両方で実行されるアプリは、入力デバイスでユーザーが選択をできるようにする、視線の先に基づくし、ポイントに基づく相互作用をサポートする必要があります。

## <a name="the-two-core-gestures-of-hololens"></a>2 つのコア HoloLens のジェスチャ

HoloLens を現在 2 つのコア コンポーネントのジェスチャの認識**エア タップ**と**ブルーム**します。 これら 2 つのコアの相互作用は、開発者がアクセスできる空間の入力データの最下位のレベルです。 これらは、さまざまなユーザーの操作の基盤を形成します。

### <a name="air-tap"></a>エア タップ

エア タップは、マウス クリックのように垂直に保持されている手でタップ ジェスチャは、または選択します。 これは、エクスペリエンスで使用ほとんど HoloLens"click"と同等の UI 要素を対象にすることで後[視線](gaze.md)します。 1 回を説明し、すべてのアプリ間で、適用する汎用的な操作になります。 1 つのボタンを押しての選択を実行するには、その他の方法は、 [HoloLens Clicker](hardware-accessories.md#hololens-clicker)または音声を話すことによってコマンドが"Select"。

![HoloLens の手のジェスチャの準備完了状態](images/image9.png)<br>
*HoloLens のエア タップの準備完了状態。*

エア タップは、不連続のジェスチャです。 選択範囲が終了したか、またはでないと、アクションまたはエクスペリエンス内では区別されません。 できますが、主要なコンポーネント (例: シングル タップとは異なる意味をダブルタップ ジェスチャ) の組み合わせから他の個別のジェスチャを作成するいくつかの特定の目的のことをお勧めします。

![準備が位置し、タップまたはクリック モーション指](images/readyandpress.jpg)<br>
*エア タップを実行する方法。準備が位置する際、人差し指をさせて、指をタップまたは選択してキーを押して解放し、バックアップします。*

### <a name="bloom"></a>「Bloom

「Bloom「ホーム」ジェスチャは、と用に予約されているだけで。 [スタート] メニューに戻るに使用されるシステムの特別な操作になります。 これは、キーボードまたは Xbox コント ローラーでは、Xbox ボタンの Windows キーを押してと同じです。 ユーザーは、いずれかの手を使用できます。

![HoloLens のブルーム ジェスチャ](images/image10-640px.png)

HoloLens にブルーム ジェスチャには、手を押しながら、palm、思い通りにまとめて。 次に、手を開きます。 メモすることができますも常にスタートに戻る言っておきたい」「コルタナさん、Go ホーム アプリは、これらのシステムによって処理されますホームのアクションに具体的には対応ことはできません。

![「Bloom ジェスチャ](images/bloom-giphy.gif)<br>
*HoloLens のブルーム ジェスチャを実行する方法。*

## <a name="composite-gestures"></a>複合のジェスチャ

アプリでは、複数の個々 のタップを認識できます。 結合をタップして保持して、リリース、手の動きより複雑な複合ジェスチャを実行できます。 これらの複合または高レベルのジェスチャは、低レベル空間からの入力データ (エア タップと Bloom) 開発者がアクセスできるに作成します。

<table>
<tr>
<th> 複合のジェスチャ</th><th> 適用する方法</th>
</tr><tr>
<td>エア タップ</td><td>エア タップのジェスチャ (およびその他のジェスチャは以下) は、特定のタップにのみ対応します。 メニューや把握などの他のタップを検出するために、アプリは、上記 2 つの重要なコンポーネントのジェスチャのセクションで説明されている下位レベルの相互作用を直接使用する必要があります。</td>
</tr><tr>
<td>タップ アンド ホールド</td><td><p>保留中のエア タップの下向きの指の位置だけ維持です。 エア タップ アンド ホールドの組み合わせによりより複雑なのさまざまな&quot; をクリックし、ドラッグ&quot;相互作用と組み合わせたときにアクティブ化することではなくオブジェクトの選択などの移動を arm または&quot;mousedown&quot;コンテキスト メニューを表示するなどのセカンダリの相互作用します。</p><p>任意拡張のジェスチャの実行中に、手の形の姿勢を緩和しやすいユーザーとしてただし、このジェスチャの設計にできる場合に、注意を使用してください。</p></td>
</tr><tr>
<td>操作</td><td><p>移動、サイズを変更する場合、ユーザーに 1 対 1 の対応するホログラム ホログラムを回転操作のジェスチャを使用できる&#39;s 手の動きです。 このような 1 対 1 の動きの 1 つの用途は、描画またはペイントの世界では、ユーザーにです。</p><p>操作のジェスチャの初期ターゲットは、視線入力または参照によって行う必要があります。 タップ アンド ホールドの開始、オブジェクトのすべての操作が、処理を手動で移動すると、操作中にユーザーを解放します。</p></td>
</tr><tr>
<td>ナビゲーション</td><td><p>ナビゲーションのジェスチャでは、仮想ジョイスティックのように動作し、放射状メニューなどの UI ウィジェットを移動に使用できます。 タップし、ジェスチャが開始され、手を中心に最初のキーを押して、正規化された 3D キューブ内に保持します。 0 の開始点の 1 に、値-1 から X、Y、Z 軸に沿った手を移動できます。</p><p>ナビゲーションは、velocity ベースの継続的なスクロールまたはズーム ジェスチャ、マウスの中央ボタンをクリックし、マウスを上下に移動して 2D の UI をスクロールすると同様の作成に使用できます。</p><p>レールを使用したナビゲーションは、その軸で特定のしきい値に達するまでは、特定の軸での動きを認識する機能を指します。 1 つ以上の軸での移動が有効な場合、アプリケーションで、開発者など、便利ですが、これはのみ、アプリケーションが X、Y 軸の間でナビゲーション ジェスチャを認識するように構成が指定されても場合 rails 軸 X。 ここでシステムが認識手の動きで X 軸の X 軸の rails (ガイド) が虚数部内にある限り、手の形の移動には、Y 軸もが発生した場合。</p><p>2D のアプリ内でユーザーは、スクロール、ズーム、またはアプリ内でドラッグ縦型ナビゲーション ジェスチャを使用できます。 これは、同じ種類のタッチ ジェスチャをシミュレートするためにアプリを仮想指タッチを挿入します。 ボタンを選択するか、というアプリ上にあるバー上のツール間で切り替えることで行われますがこれらのアクションのユーザーが選択できる&#39;&lt;スクロール/ドラッグ/ズーム&gt;ツール&#39;します。</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>ジェスチャ レコグナイザー

ジェスチャ認識を使用して 1 つの利点は、現在のターゲット ホログラムが受け入れることができるジェスチャのジェスチャ認識エンジンを構成することができます。 プラットフォームでは、これらの特定のサポートされているジェスチャを区別するために必要な曖昧のみを行います。 そうすることだけエア タップをサポートするホログラムは任意の長さのキーを押してからリリースまでの時間を受け入れることができます、ホログラム中をサポートしています をタップし、の両方を保持できます後を昇格させる保留をタップして、ホールド時間のしきい値。

## <a name="hand-recognition"></a>手の形の認識

HoloLens では、デバイスに表示されているいずれかまたは両方のハンドの位置を追跡して手のジェスチャを認識します。 いずれかの場合、HoloLens は手を表示、**準備状態**(背面人差し指をに向けてして手のアイコン)、または**状態の押された**(背面インデックス指でに向けてして手のアイコン)。 手が他が発生する場合、それら、HoloLens は無視されます。

各ハンドの HoloLens を検出すると、(向き) なしの位置と、押された状態にアクセスすることができます。 して手のアイコンは、ジェスチャのフレームの端に近いが再び HoloLens が表示できる場所を取得するには、その手を移動する方法を把握できるように、ユーザーに表示できる方向ベクトルも与えられます。

## <a name="gesture-frame"></a>ジェスチャ フレーム

HoloLens のジェスチャは、フレーム内で"ジェスチャ"、(非常に大まかにウェストと肩の間での鼻) からジェスチャ検知カメラが適切に参照できる範囲内でして手のアイコン必要があります。 ユーザーは、認識操作の成功と独自の快適性の両方が (多くのユーザーが最初と仮定ジェスチャ フレームが HoloLens、これにより、ビュー内であるし、対話するには多く自分の腕を保持する必要があります) のこの領域でトレーニングを受ける必要があります。 HoloLens Clicker を使用する場合は、手をジェスチャ フレーム内である必要はありません。

継続的なジェスチャの場合具体的がユーザーの中には、(中に何らかの holographic オブジェクトを移動するなど) の中間のジェスチャ、ジェスチャのフレームの外部で手に移動し、目的の結果を失うことのリスクです。

考慮すべき 3 つのことがあります。
* ジェスチャのフレームの存在とおおよその境界 (これは、HoloLens のセットアップ中については) でユーザー教育します。
* ときに、ジェスチャが近づいて/重大な程度失わジェスチャが望ましくない結果に至るまで、アプリケーション内でジェスチャ フレーム境界のユーザーに通知します。 調査によれば、このような通知システムのキーの品質を評価し、HoloLens のシェルがこの (ビジュアルでは、どの境界の交差が行われて方向を示す、中央のカーソルで) 通知の種類の良い例を提供します。
* ジェスチャのフレームの境界線の重大な影響を最小限に抑える必要があります。 一般はジェスチャの結果が、境界で停止していることが逆になっていないを意味します。 などの場合は、ユーザーが、部屋の holographic によってオブジェクトを移動、移動を停止、ジェスチャのフレームが違反になった場合が**いない**出発点に返されます。 ユーザーは、可能性がありますし、いくつかのストレスが発生するが可能性があります、境界がより迅速に理解していなくてたびに完全な意図した操作を再起動します。

## <a name="see-also"></a>関連項目
* [視線の先を対象とします。](gaze-targeting.md)
* [音声のデザイン](voice-design.md)
* [MR 入力 211:ジェスチャ](holograms-211.md)
* [ジェスチャと Unity のアニメーション コント ローラー](gestures-and-motion-controllers-in-unity.md)
* [視線、ジェスチャ、および DirectX でモーション コント ローラー](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [アニメーション コント ローラー](motion-controllers.md)