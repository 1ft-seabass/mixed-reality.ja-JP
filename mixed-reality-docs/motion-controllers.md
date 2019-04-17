---
title: アニメーション コント ローラー
description: Mixed Reality アニメーション コント ローラーについて説明します。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6 dof コント ローラー、モーションのコント ローラー
ms.openlocfilehash: b44964ab872bd080349ecf1b04b3f7082b521a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604961"
---
# <a name="motion-controllers"></a>アニメーション コント ローラー

アニメーション コント ローラーが[ハードウェア アクセサリ](hardware-accessories.md)複合現実でアクションを実行するユーザーを許可します。 モーションのコント ローラー上の利点[ジェスチャ](gestures.md)コント ローラーでは、空間における正確な位置がデジタル オブジェクトの細かいやり取りすることができます。 Windows Mixed Reality イマーシブ ヘッドセット、アニメーション コント ローラーはユーザーは自分の世界で対処する主な方法です。

![Windows Mixed Reality モーションのコント ローラー](images/winmr-ck-1080x1080-350px.jpg)


## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> アニメーション コント ローラー</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>ハードウェアの詳細

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Windows Mixed Reality モーションのコント ローラーは、つまり自分のスペースでの壁面にハードウェアをインストールする必要はありません、イマーシブ ヘッドセットのセンサーを使用して、フィールドのビューでの移動の追跡を正確かつ応答性を提供します。 これらのアニメーション コント ローラーは、セットアップと Windows Mixed Reality イマーシブ ヘッドセットと移植性の同じくらい簡単に提供されます。 により、デバイス パートナーを計画し、この休日の発売にこれらのコント ローラーを販売します。

![コント ローラーを理解します。](images/controllerimage-750px.png)<br>
*コント ローラーを理解します。*

**機能:**
* 光の追跡
* トリガー
* ボタンを取得します。
* スティック
* タッチパッド

## <a name="setup"></a>セットアップ

### <a name="before-you-begin"></a>始める前に

**必要があります。**
* 2 つのアニメーション コント ローラーのセット。
* AA バッテリの 4 つです。
* Bluetooth 4.0 できる PC。

**Windows、Unity、およびドライバーの更新プログラムの確認**
* 参照してください[ツールをインストールする](install-the-tools.md)優先のバージョンの Windows では、Unity、複合現実の開発のためなどです。
* 最も最新の状態があるかどうかを確認[ヘッドセットおよびモーションのコント ローラー ドライバー](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)します。

### <a name="pairing-controllers"></a>コント ローラーのペアリング

アニメーション コント ローラーは、ホスト PC と結合できます、他の Bluetooth デバイスのように Windows の設定を使用します。

1. コント ローラーの背面に 2 つの AA バッテリを挿入します。 ここではバッテリ カバーを省略します。
2. 組み込みの Bluetooth 無線ではなく、外部 USB Bluetooth アダプターを使用する場合は確認してください、 [Bluetooth のベスト プラクティス](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)続行する前にします。 組み込みの無線とデスクトップの構成、アンテナが接続されているを確認してください。
3. 開いている**Windows 設定** -> **デバイス** -> **Bluetooth の追加または他のデバイス** -> **Bluetooth**および「アニメーション コント ローラー: 右」と「モーション コント ローラー – 左」のすべての以前のインスタンスを削除します。 さらに、一覧の下部にあるその他のデバイス カテゴリを確認します。
4. 選択**Bluetooth の追加または他のデバイス**開始 Bluetooth デバイスを検出することを確認します。
5. コント ローラーを 1 回、解放 buzzes コント ローラーの Windows ボタンを押したままにします。
6. プレス アンド ホールド Led までペアリング ボタン (バッテリ コンパートメント内 タブ) は、パルスを開始します。
7. 「モーション コント ローラー - 左」または「アニメーション コント ローラー - 右」を待機するリストの下に表示されます。 ペアを選択します。 接続されている場合、コント ローラーが 1 回振動します。

   ![複数のインスタンスは、一覧の表示の一番下から 1 つを選択する場合は、モーションのコント ローラーのペアを選択します](images/450px-bluetooth-add-a-device-300px.png)<br>
   *ペアに「モーションのコント ローラー」を選択します複数のインスタンスがある場合、一覧の下部にあるいずれかを選択します。*
   
8. Bluetooth の設定に表示するコント ローラーが表示されます **「マウス、キーボード、およびペン」カテゴリ**として**接続**します。 この時点では、ファームウェアの更新プログラム – してしまうを参照してください[次のセクション](motion-controllers.md#updating-controller-firmware)します。
9. バッテリのカバーを再アタッチします。
10. 2 番目のコント ローラーの手順 1 ~ 9 を繰り返します。

設定なります両方のコント ローラーを正常にペアリングするには後でこのような **「マウス、キーボード、およびペン」カテゴリ** 

   ![接続されているアニメーション コント ローラー](images/450px-motion-controller-connected-300px.png)<br>
   *接続されているアニメーション コント ローラー*

ペアリングした後、コント ローラーがオフの場合、それらの状態が対応のあるとして表示されます。 コント ローラーは、「その他のデバイス」カテゴリのペアリングが部分的にのみ完了したとコント ローラーの機能を取得するもう一度実行する必要が完全に維持します。 場合、

### <a name="updating-controller-firmware"></a>コント ローラーのファームウェアを更新しています

* イマーシブ ヘッドセットが、PC に接続して、新しいコント ローラーのファームウェアが使用可能な場合は、ファームウェアにプッシュされます、アニメーション コント ローラーに自動的に有効にして [次へ] の時刻。 コント ローラー ファームウェアの更新プログラムは、円を描く、わかりやすい LED の四分区間のパターンで示され、1 ~ 2 分かかります。
* ファームウェアの更新が完了した後、コント ローラーが再起動し、再接続します。 両方のコント ローラーを今すぐに接続する必要があります。 
    
    ![接続されているコント ローラー](images/cyk-connected-300px.jpg)<br>
    *Bluetooth の設定で接続されているコント ローラー*

* 正しくコント ローラーの作業内容を確認します。
    1. 起動**Mixed Reality ポータル**自宅 Mixed Reality を入力します。
    2. コント ローラーに移動して追跡、[test] ボタンを確認し、確認[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)動作します。 場合は、チェック アウトされない、[コント ローラーのトラブルシューティングのモーション](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)します。

## <a name="gazing-and-pointing"></a>Gazing とポイント

Windows Mixed Reality は、対話の 2 つの主なモデルをサポートしている**された様子を確認し、コミット**と**をポイントし、コミット**:
* **された様子を確認し、コミット**、ユーザー対象のオブジェクト、[視線](gaze.md)し手の形のエア タップ、ゲームパッド、clicker または音声を持つオブジェクトを選択します。
* **をポイントし、コミット**ユーザーがターゲット オブジェクトでのポイントに対応したモーション コント ローラーのことを目的し、コント ローラーのトリガーを持つオブジェクトを選択します。

サポート モーションのコント ローラーを指す必要がありますもアプリは、可能であれば注視駆動の相互作用を有効にするでどのような選択肢をユーザーに付与するには、入力のデバイスを使用します。

### <a name="managing-recoil-when-pointing"></a>ポイントしたときに、recoil を管理します。

アニメーション コント ローラーをポイントし、コミットを使用する場合、ユーザーは対象し、し、そのトリガーを引いて、アクションを実行するコント ローラーを使用します。 トリガーを徹底的にプルするユーザーは、ことを目的としたよりも高い、トリガ プルの最後に、コント ローラーの狙いを定める最終的可能性があります。

ユーザー トリガーをプルするときに発生するこのような recoil を管理するには、トリガーのアナログの軸の値が 0.0 を超えたときに、アプリがそのターゲット レイをスナップすることができます。 使用してアクションを対象とするレイ フレームをいくつか後でトリガーの値に達する 1.0 では、短い形式の時刻ウィンドウ内で最後のキーを押してが発生した場合に限りを実行できます。 高レベルを使用する場合[複合タップ ジェスチャ](gestures.md#composite-gestures)Windows を管理するこのレイ キャプチャとタイムアウトの対象します。

## <a name="grip-pose-vs-pointing-pose"></a>グリップの姿勢ポインティング ポーズとの比較

Windows Mixed Reality は、さまざまなフォーム ファクターでモーションのコント ローラーをサポートしている、各コント ローラーの設計と、ユーザーの手の形の位置とそのアプリの方向を「転送」自然の間の関係の違いポイントを表示するときに使用する必要があります、コント ローラー。

これらのコント ローラーをより適切に表すには、2 種類の各相互作用ソースを調査することができますが発生、**グリップ姿勢**と**ポインター姿勢**します。

### <a name="grip-pose"></a>グリップの姿勢

**グリップ姿勢**HoloLens、によって検出された手の形の palm またはアニメーション コント ローラーを保持している片手で行うことのいずれかの場所を表します。

レンダリングに使用最適グリップ姿勢でイマーシブ ヘッドセット、**ユーザーの手**または**オブジェクトは、ユーザーの手の形で保持されている**剣ガンなど、します。 グリップの姿勢は、として、アニメーション コント ローラーを視覚化するときにも使用、**レンダリング可能なモデル**運動の Windows で、コント ローラーは、送信元と回転の中心としてグリップ姿勢を使用して指定します。

グリップ姿勢が具体的には次のように定義されています。
* **位置を握って**:Palm 重心当然ながら、コント ローラーを保持しているときに、左または右中央にグリップ内の位置を調整します。 Windows Mixed Reality アニメーション コント ローラーで、この位置は把握ボタンで一般に揃えて配置します。
* **向きの適切な軸を握って**:5 本の指フラットな姿勢を形成する完全に開くと、射線は、palm に通常 (順方向から左 palm、適切な palm から旧バージョンとの)
* **向きの順方向軸を握って**:部分的に (場合と同様、コント ローラーを保持している) の手の閉じるときに、"forward"チューブを通じて非 thumb 指によって形成されるポイントの半径。
* **軸の向きを握って**:右と前方参照の定義が含まれるアップ軸。

### <a name="pointer-pose"></a>ポインターの姿勢

**ポインター姿勢**フォワード指し示すコント ローラーの先端を表します。

システム指定のポインターの姿勢はしたら、最適な raycast に使用**コント ローラー モデル自体のレンダリング**します。 仮想の銃など、コント ローラーの代わりにその他の仮想オブジェクトをレンダリングする場合は光線ガンのアプリで定義されたモデルの軸に沿って移動するなど、その仮想オブジェクトの最も自然なレイでポイントする必要があります。 仮想オブジェクトと物理のコント ローラーではないユーザーが表示できるため、仮想オブジェクトでポイントがあります、アプリを使用してこれらのより自然です。

## <a name="controller-tracking-state"></a>コント ローラーの状態の追跡

ヘッドセットなど、Windows Mixed Reality モーションのコント ローラーの外部の追跡のセンサーのセットアップは必要ありません。 代わりに、コント ローラーは、ヘッドセット自体のセンサーによって追跡されます。

場合は、ユーザーは、ヘッドセットのビューのフィールドからコント ローラーを移動、ほとんどの場合 Windows 引き続きコント ローラーの位置を推測し、アプリに提供されます。 ときに、コント ローラーの位置を正確度のおおよその位置にドロップは、十分な時間のビジュアルの追跡、コント ローラーを失いました。

この時点では、システムは、本文ロックをコント ローラーをユーザーに、その内部方位センサーを使用して、コント ローラーの場合は true。 向きを引き続き公開中に移動する場合に、ユーザーの位置を追跡します。 ポイントし、UI 要素をアクティブ化するコント ローラーを使用する多くのアプリが、ユーザーのルーティング グループおおよその精度で通常どおり操作できます。

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>明示的に状態の追跡についての考え方

位置に応じて異なる状態の追跡を処理するアプリは、さらに移動し、SourceLossRisk や PositionAccuracy などのコント ローラーの状態でプロパティを調べることがあります。

<table>
<tr>
<th> 状態の追跡 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精度 (損失の危険)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>おおよその精度</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>位置</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: orange"> false</td>
</tr>
</table>



これらのアニメーション コント ローラー追跡状態の定義は次のとおりです。
* **高精度は:** ヘッドセットのビューのフィールド内のモーション コント ローラーは、中には、高精度の位置、ビジュアルの追跡に基づく一般に提供します。 注移動コント ローラーを一時的にビューのフィールドのままにヘッドセット センサーから一時的に隠されている (などによって、ユーザーの一方) を返すコント ローラーの慣性による追跡に基づく、短時間、高精度ポーズは引き続き自体。
* **(データが失われる危険性) が高精度は:** ユーザーは、過去のヘッドセットの視野の edge モーション コント ローラーを移動したとき、ヘッドセットすぐにできなくコント ローラーの位置を視覚的に追跡するためにします。 アプリが、コント ローラーが達したらこの FOV 境界を見ることによって、 **SourceLossRisk** 1.0 に到達します。 その時点では、アプリは、コント ローラーのジェスチャを非常に高品質なポーズの流れを必要とするを一時停止する選択できます。
* **近似精度は:** ときに、コント ローラーの位置を正確度のおおよその位置にドロップは、十分な時間のビジュアルの追跡、コント ローラーを失いました。 この時点では、システムは、本文ロックをコント ローラーをユーザーに、その内部方位センサーを使用して、コント ローラーの場合は true。 向きを引き続き公開中に移動する場合に、ユーザーの位置を追跡します。 ポイントし、UI 要素をアクティブ化するコント ローラーを使用する多くのアプリは、ユーザーのルーティング グループおおよその精度で通常 while として動作できます。 やや入力要件がアプリからこのドロップを理解することもできます**高**精度**Approximate**精度を調べることによって、 **PositionAccuracy**プロパティのこの期間中に画面外のターゲットについて、ユーザー寛大な hitbox を提供する例です。
* **位置:** コント ローラーは、おおよその精度で長時間動作、中に場合があります、システムを知っていることも、本文ロック位置が意味のある現時点で。 など、コント ローラーだけを有効にする可能性がありますことはありませんされてまたは計測される視覚的に、ユーザーが、他のユーザーによってピックアップされるコント ローラーを設定します。 これらのタイミングで、システムが提供しないアプリに任意の位置と**TryGetPosition**は false を返します。

## <a name="interactions-low-level-spatial-input"></a>相互作用:空間の低レベルの入力

手およびモーションのコント ローラーの間で主要な相互作用が**選択**、**メニュー**、**持ち**、**タッチパッド**、 **スティック**、および**ホーム**します。
* **選択**はリリース後にキーを押してから成る、ホログラムをアクティブ化する主な操作です。 アニメーション コント ローラーの選択のキーを押して、コント ローラーのトリガーを使用してを実行します。 選択を実行するその他の方法が話すことによっては、[音声指示コマンド](voice-input.md)"Select"です。 同じ 相互作用は、すべてのアプリで使用できます。 同等のマウス クリックすると、1 回を説明し、すべてのアプリ間で、適用する汎用アクションとして選択の検討します。
* **メニュー**は、コンテキスト メニューまたはその他のセカンダリ操作に使用するオブジェクトの操作を行うのためのセカンダリの操作です。 アニメーション コント ローラーには、コント ローラーを使用してメニュー アクションを実行できる*メニュー*ボタンをクリックします。 (つまりにハンバーガー「メニュー」アイコンが付いたボタン)
* **持ち**がどのようにユーザー直接アクションを実行できるオブジェクトを操作するため、手の形でします。 アニメーション コント ローラーと緊密に、最初をつかんで、把握アクションを行うことができます。 アニメーション コント ローラーには、グラブ ボタン、palm トリガー、またはその他のセンサーの理解を検出可能性があります。
* **タッチパッド**タッチパッドのをクリックして、操作を実行するアニメーション コント ローラーのタッチパッドの 2 次元表面上でアクションを調整できます。 タッチパッドでは、押された状態、影響を受ける状態および正規化の XY 座標を提供します。 センターで、循環タッチパッドの範囲全体で 1 を-1 から X と Y の範囲 (0, 0)。 X、-1 は、左に、1 は、右にします。 Y の下にある-1 と 1 は、上位。
* **スティック**スティックのをクリックして、操作を実行するアニメーション コント ローラーのスティックが循環の範囲内で移動することで 2 つのディメンション内のアクションを調整できます。 サムスティックも押された状態を提供し、XY 座標を正規化します。 センターで、循環タッチパッドの範囲全体で 1 を-1 から X と Y の範囲 (0, 0)。 X、-1 は、左に、1 は、右にします。 Y の下にある-1 と 1 は、上位。
* **ホーム**は [スタート] メニューに戻るに使用される特殊なシステム アクションです。 キーボードまたは Xbox コント ローラーでは、Xbox ボタンの Windows キーを押してに似ています。 アニメーション コント ローラーの Windows ボタンを押して、帰宅ことができます。 メモすることができますも常にスタートに戻る言っておきたい」「コルタナさん、Go ホーム アプリは、これらのシステムによって処理されますホームのアクションに具体的には対応ことはできません。

## <a name="composite-gestures-high-level-spatial-input"></a>複合のジェスチャ。高度な空間の入力

両方[ジェスチャを渡す](gestures.md)モーションのコント ローラーは、高レベルの共通セットを検出するために時間の経過と共に追跡できますと**[複合ジェスチャ](gestures.md#composite-gestures)** します。 これにより、アプリを高度な検出**タップ**、**保持**、**操作**と**ナビゲーション**ジェスチャを使用してユーザーを終了かどうか手やコント ローラー。

## <a name="rendering-the-motion-controller-model"></a>レンダリング、アニメーション コント ローラー モデル

**コント ローラーの 3D モデル**Windows により、アプリで使用できる各アニメーション コント ローラーのレンダリング可能なモデル、システムで現在アクティブにします。 動的に読み込まれ、実行時にこれらのシステム指定のコント ローラー モデルを明示するアプリで、アプリがその後に順方向と互換性のあるコント ローラーの設計を保証できます。

これらのレンダリング可能なモデルがすべてで描画される、**グリップ姿勢**、コント ローラーのモデルの原点としてに揃えて配置されます、物理世界では、このポイント。 コント ローラー モデルをレンダリングする場合たい場合がありますし、raycast からシーンに、**ポインター姿勢**、沿ったユーザーが自然な期待をポイントするコント ローラーの物理的なデザインを指定された射線を表します。

Unity で動的にコント ローラー モデルを読み込むための方法の詳細については、次を参照してください。、 [Unity でモーション コント ローラー モデルをレンダリング](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity)セクション。

**コント ローラーの 2D ライン アート**アプリ内のコント ローラーのヒントとコマンドをアプリ内のコント ローラー モデル自体にアタッチすることをお勧め、中に一部の開発者は、フラット「チュートリアル」または「方法」でモーション コント ローラーの 2D ライン アートの表現を使用する可能性がありますUI。 これらの開発者は、.png モーション コント ローラー ライン アート ファイル以下黒と白が両方で使用可能な (右クリックして保存) を行いました。

![アニメーション コント ローラーのライン アートのプレビュー](images/motioncontrollers-black-preview-300px.png)

 [線のアートのフル解像度のモーションのコント ローラー '' 白い ' '](images/motioncontrollers-white.png)
 
 [線のアートのフル解像度のモーションのコント ローラー '' 黒 ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>FAQ

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>コント ローラーを複数の Pc はペア モーションできますか。

モーションのコント ローラーは、1 台の PC とのペアリングをサポートします。 指示に従って[コント ローラーのセットアップのモーション](motion-controllers.md#setup)コント ローラーとペア。

### <a name="how-do-i-update-motion-controller-firmware"></a>アニメーション コント ローラーのファームウェアの更新方法

アニメーション コント ローラーのファームウェア、ヘッドセット ドライバーの一部でありは自動的に更新接続に必要な場合。 ファームウェアの更新プログラムは、通常、Bluetooth のオプション ボタンやリンクの品質に応じて 1 ~ 2 分をかかります。 まれに、コント ローラー ファームウェアの更新プログラムは最大 10 分間、低性能な Bluetooth 接続または無線の干渉を示していることをかかる場合があります。 参照してください[熱心なユーザー ガイドで Bluetooth のベスト プラクティス](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)接続の問題のトラブルシューティングを行う。 ファームウェアの更新後にコント ローラーが再起動し、ホスト (移動の追跡の明るい Led にお気付き) PC に再接続します。 ファームウェアの更新プログラムが中断された場合 (たとえば、コント ローラーは電源を失われます)、コント ローラーの電源が入ってときにもう一度、試行されます。

### <a name="how-i-can-check-battery-level"></a>どのようにバッテリ レベルをチェックはできるでしょうか。

[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)、仮想モデルの裏側にそのバッテリ レベルを表示する経由でコント ローラーを有効にすることができます。 物理的なバッテリ レベル インジケーターはありません。

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>ヘッドセットことがなくこれらのコント ローラーを使用できますか。 だけ入力の場合、ジョイスティック、トリガーなどですか。

ユニバーサル Windows アプリケーション。

## <a name="troubleshooting"></a>トラブルシューティング

参照してください[コント ローラーのトラブルシューティングのモーション](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)熱心なユーザー ガイドです。

## <a name="filing-motion-controller-feedbackbugs"></a>アニメーション コント ローラーからのフィードバック/バグの報告

[フィードバックを提供](give-us-feedback.md)フィードバック ハブで、「Mixed Reality は、入力を ->"カテゴリを使用します。

## <a name="see-also"></a>関連項目
* [ジェスチャと Unity のアニメーション コント ローラー](gestures-and-motion-controllers-in-unity.md)
* [視線、ジェスチャ、および DirectX でモーション コント ローラー](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [ジェスチャ](gestures.md)
* [MR 入力 213:アニメーション コント ローラー](mixed-reality-213.md)
* [愛好家のガイド:Home、Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [愛好家のガイド:Windows Mixed Reality でのゲームとアプリの使用](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [徹底解剖の追跡のしくみ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)