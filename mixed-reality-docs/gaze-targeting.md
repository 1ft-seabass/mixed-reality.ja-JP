---
title: 視線の先を対象とします。
description: すべての対話は、ユーザーの入力モードに関係なく、対話する要素を対象とする機能に基づいて構築します。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 実際には、視線の先、対象とする操作、視線の先を混合の設計します。
ms.openlocfilehash: c3225e27331f8afcda65469eb84fe5470bf6ee8c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600681"
---
# <a name="gaze-targeting"></a>視線の先を対象とします。

すべての対話は、ユーザーの入力モードに関係なく、対話する要素を対象とする機能に基づいて構築します。 Windows Mixed Reality でこれは、一般に、ユーザーの視線の先を使用します。

エクスペリエンスを正常に使用するユーザーを有効にするには、ユーザーの目的、およびユーザーの実際のインテントのシステムの計算については、できる限り忠実に従う必要があります。 程度にシステムがユーザーの意図した操作を解釈する正しく、満足度が増えるとパフォーマンスが向上します。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> 視線の先を対象とします。</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️ </td>
</tr><tr>
<td> 監視対象とします。</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。

## <a name="target-sizing-and-feedback"></a>ターゲットのサイズ変更とフィードバック

視線入力ベクトルは正しく対象とするために使用するのには繰り返し示されていますが、gross ターゲット (取得若干大きくターゲット) に最も適した多くの場合。 1.5 に 1 度の最小のターゲットのサイズは、3 度のターゲットが多くの場合より高速化を使用する場合、ほとんどのシナリオで成功したユーザーの操作を許可する必要があります。 注いる対象ユーザーは 3D 要素の場合でも 2D 領域では効果的にサイズどのプロジェクションが直面する、ターゲット設定可能な領域があります。 要素が「アクティブ」(こと、ユーザーが対象にすること) があるいくつかの注目すべきキューが非常に役立つ - これを含めることができますを提供する処理などの表示「ホバー」効果やオーディオのハイライト、 をクリックまたは要素を使用してカーソルの配置をオフにします。

![2 つのメーター距離にある最適なターゲット サイズ](images/gazetargeting-size-1000px.jpg)<br>
*2 つのメーター距離にある最適なターゲット サイズ*

![視線の先の対象となるオブジェクトを強調表示の例](images/gazetargeting-highlighting-640px.jpg)<br>
*視線の先の対象となるオブジェクトを強調表示の例*

## <a name="target-placement"></a>ターゲットの配置

ユーザーは、多くの場合、(通常は約監視レベル) にフォーカスがメインの周囲の領域で、注意のほとんどに重点を置いて、視野で非常に高または非常に低配置されている UI 要素を検索する失敗します。 目のレベルによって適切なバンドでほとんどのターゲットを配置することができます。 ユーザーの傾向を与え、比較的小さな視覚的な領域 (ビジョンの attentional コーンは 10 度では約) いつでも、概念的に関連している度合いをまとめて UI 要素をグループに重点を活用できますから注意順行連鎖の動作項目のユーザーとして領域を通じて、視線の先に移動します。 UI を設計するときは、HoloLens、イマーシブ ヘッドセットとビューのフィールドに潜在的な大規模なバリエーションに注意してください。

![Galaxy エクスプ ローラーで対象とする簡単視線の先のグループ化された UI 要素の例](images/gazetargeting-grouping-1000px.jpg)<br>
*Galaxy エクスプ ローラーで対象とする簡単視線の先のグループ化された UI 要素の例*

## <a name="improving-targeting-behaviors"></a>ターゲットの動作の向上

何かを対象とするユーザーの意図を確認 (または密接に近似)、「ニアミス」が正しくを対象としていた場合と同様の対話に試行を受け入れるように非常に便利ですができます。 複合現実エクスペリエンスに組み込むことが成功したメソッドのいくつかあります。

### <a name="gaze-stabilization-gravity-wells"></a>視線入力安定化 ("重力 wells")

これが有効にする時間のほとんどまたはすべて。 この手法は、自然な head/ネック ジッター可能性のあるユーザーを削除します。 検索読み上げの動作が原因も移動します。

### <a name="closest-link-algorithms"></a>最も近いリンク アルゴリズム

これらは、スパースの対話型コンテンツ領域に最適な機能します。 対話する試行がユーザーを決定することができます可能性が高い場合は、単に一定レベルのインテントを想定して、ターゲットの能力を補うことができます。

### <a name="backdatingpostdating-actions"></a>Backdating 遅延アクション

このメカニズムは、速度が必要なタスクに役立ちます。 ユーザーは、一連の対象とする、アクティブ化の最適経路の速度で移動が、いくつかの目的を想定し、許可すると便利できます*手順が実行されなかった*ユーザーがいたフォーカスで若干の前後に若干タップ (ターゲットに対して操作を実行するには50 ミリ秒の前に、/後が初期テストで有効になります)。

### <a name="smoothing"></a>スムージング

このメカニズムは、パスの移動、ヘッドの移動を自然な特性のため若干のジッター/補助の削減に役立ちます。 パスのモーション、時間の経過と共にではなく、動きの距離のサイズでスムーズに円滑化するとき

### <a name="magnetism"></a>磁力

このメカニズムはターゲットに向かって、カーソルを描画するか、単に (視覚的またはない) かどうかに hitboxes を増やす「リンクでは最も近い」アルゴリズムの一般的なバージョンとして考えることができます可能性の高い目標を実現するユーザーに、使用する対話型のレイアウトの知識優れたアプローチ ユーザーのものです。 これは、小規模のターゲットの非常に強力なことができます。

### <a name="focus-stickiness"></a>フォーカスの持続性

フォーカスを移す対話型の要素の近くに判断する、現在フォーカスが要素に、バイアスを提供します。 これは自然なノイズを含む 2 つの要素間の中間に浮動小数点の動作の切り替えが不規則のフォーカスの削減に役立ちます。

## <a name="see-also"></a>関連項目
* [ジェスチャ](gestures.md)
* [音声のデザイン](voice-design.md)
* [カーソル](cursors.md)