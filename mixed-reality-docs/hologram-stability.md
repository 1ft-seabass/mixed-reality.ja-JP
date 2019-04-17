---
title: ホログラム安定性
description: HoloLens はホログラム、自動的に安定しますが、開発者はホログラムの安定性をさらに向上させるために実行できる手順があります。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: ホログラム、安定性、hololens
ms.openlocfilehash: 9b0227102934650d5640a4ac1c4d6f59ecd8e6dd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600771"
---
# <a name="hologram-stability"></a>ホログラム安定性

安定したホログラムを実現するためには、HoloLens は、組み込みイメージ安定化パイプラインを持ちます。 有効にするために必要な追加の手順がないために、安定化パイプラインは、バック グラウンドで自動的に動作します。 ただし、開発者はホログラム安定性が向上する方法を練習し、安定性を軽減するためのシナリオを回避する必要があります。

## <a name="hologram-quality-terminology"></a>ホログラム品質用語

ホログラムの品質は、適切な環境と適切なアプリ開発の結果です。 ヒット、定数 60 フレームで 1 秒あたりの HoloLens が、周辺の状況を追跡できる環境でアプリのようになります、ホログラムと一致する座標系が同期。ユーザーの観点から、環境の基準とした静止するものではホログラムは移動されません。

環境の問題は、一貫性のない、または低のレンダリング速度、またはその他のアプリの問題表示、次の用語は、問題を特定するのに役立つ。
* **精度。** ホログラムが世界ロックされ、現実の世界に、これが配置された、ユーザー動作や、スパースの環境の変更に依存しない周辺環境に対して相対的に維持する必要があります。 ホログラムが後で、予期しない場所に表示された場合は、*精度*問題。 このようなシナリオは、2 つの個別の部屋が似ている場合に発生します。
* **変位。** ユーザーは、高頻度はホログラムの振動としてこれを確認します。 これは、環境の追跡が低下する場合に発生します。 ユーザーは、ソリューションが実行されている[センサー チューニング](sensor-tuning.md)します。
* **ジャダーします。** 不均一なモーション センサーとホログラムの二重イメージ レンダリングの低周波数発生します。 モーションとホログラムで特に顕著になります。 開発者が管理する必要があります、[定数 60 FPS](hologram-stability.md#frame-rate)します。
* **誤差。** ユーザーに見えるようにホログラムが格納されたから脱却するために表示されます。 これからホログラムが遠くに配置するときに発生[空間アンカー](spatial-anchors.md)、特にで完全にマップされていない環境の部分。 空間アンカーに近いホログラムを作成するには、誤差が発生する可能性が低くなります。
* **Jumpiness します。** ホログラムが「表示」または「ジャンプ」の場所から随時場合。 これは、追跡、環境の更新の理解と一致するホログラムを調整するように発生することができます。
* **スイムレーン。** ときにユーザーの頭の動きに対応する sway にホログラムが表示されます。 これはホログラムに追加していないときに発生します。、[安定化平面](hologram-stability.md#stabilization-plane)、、HoloLens でない場合、[調整](calibration.md)、現在のユーザー。 ユーザーを再実行、[調整](calibration.md)これを解決するアプリケーション。 開発者は、安定性をさらに強化するために、安定化プレーンを更新できます。
* **色の分離。** HoloLens で表示は、60 hz (240 Hz でフィールドが示すように個々 の色) の赤、緑、青の緑のカラー チャネルをフラッシュする色の順次表示です。 ユーザーは、自分の目に移動ホログラムを追跡しているときにそのホログラムのリード エッジやトレーリング エッジ虹の効果を作成、構成のカラーで区切ります。 分離の度合いは、ホログラムの速度に依存します。 いくつかのまれな場合に、静止ホログラムしている間に迅速に head が虹の効果も可能性ものを移動します。 これは呼び出されます*[色の分離](hologram-stability.md#color-separation)* します。

## <a name="frame-rate"></a>フレーム レート

フレーム レートはホログラム安定性の最初の柱です。 ホログラム、世界中に安定して表示する、ユーザーに表示される各イメージはホログラムの正しい場所に描画が必要です。 HoloLens 更新 240 時間を秒で表示には、イメージ、60 FPS (1 秒あたりのフレーム数) のユーザー エクスペリエンスを新しく、それぞれの 4 つの個別の色のフィールドを示す表示されます。 考えられる最善のエクスペリエンスを提供するには、アプリケーション開発者はこれに 16 ミリ秒ごとにオペレーティング システムに新しいイメージを一貫して提供する変換、60 FPS を維持しなければなりません。

**60 FPS** HoloLens を現実の世界に座っていると同様に見えるホログラムを描画するには、ユーザーの位置から画像を表示する必要があります。 イメージのレンダリングに時間がかかるため、イメージは、表示に表示されるとき、ユーザーの頭のある HoloLens を予測します。 この予測アルゴリズムは、簡略化したものです。 HoloLens では、予測のヘッドの位置と実際のヘッドの位置の不一致についてアカウントに描画された画像を調整するハードウェアがあります。 適切な場所からレンダリングされた、ホログラムが安定したと思われる場合とをこれにより、イメージ、ユーザーが表示されますが表示されます。 イメージを更新作業最も小さな変更をしモーション視差のように表示されるイメージには特定の点を完全に修正することはできません。

によって 60 FPS でレンダリングでは、安定したホログラムを実現する 3 つのことを行います。
1. イメージと、ユーザーに表示されるイメージのレンダリングの間の全体的な待機時間を最小限に抑えます。 ゲームのスレッドとレンダリング スレッドのエンジンでは、30 FPS で実行されている現在実行されているは、余分な待機時間の 33.3ms に追加できます。 待機時間を減らすことで、これは予測のエラーが低下し、ホログラム安定性が向上します。
2. ユーザーの目に到達するすべてのイメージが待機時間、一貫性のある時間になります。 30 fps でレンダリングする場合、表示により、その 60 FPS で引き続きイメージが表示されます。 つまり、行に 2 回、同じ画像が表示されます。 2 番目のフレームは 16.6 ミリ秒ですが、最初のものより多くの待機時間枠をおよび勝って量のエラーを修正する必要があります。 この不整合エラー絶対値では、60 hz ジャダーが望ましくない可能性があります。
3. ジャダーの外観を減らすことが特徴は、不均一なモーション センサーと二重のイメージ。 レートがより顕著に関連付けられている高速ホログラム モーション センサーと下位レンダリング judder します。 そのため、60 FPS を保持するために回避けることができますを指定した移動ホログラム ジャダーします。

**フレーム レートの一貫性**フレーム レートの一貫性は、高フレーム-1 秒あたりのと同じくらい重要です。 削除、フレームは、任意のコンテンツが豊富なアプリケーションの避けられないと、HoloLens は不定期の問題から復旧するいくつかの高度なアルゴリズムを実装します。 ただし、絶えず変動のフレーム レートは下のフレーム レートで一貫して実行するよりも、ユーザーにもっと顕著です。 たとえば、5 つのフレーム (これら 5 つのフレームの間に 60 FPS) の円滑にレンダリングし、次の 10 個のフレーム数 (これら 10 フレームの間に 30 FPS) が表示されますが、アプリケーションよりもより不安定な一貫している他のすべてのフレームを削除するアプリケーション30 FPS をレンダリングします。

オペレーティング システムに関連して、アプリケーションを 30 FPS を制限するときに[実際のキャプチャを混合](mixed-reality-capture.md)が実行されています。

**パフォーマンス分析**はさまざまなツールなど、アプリケーションのフレーム レートのベンチマークを実行するために使用できます。
* GPUView
* Visual Studio のグラフィックス デバッガー
* Unity などの 3D エンジンに組み込まれているプロファイラー

## <a name="hologram-render-distances"></a>ホログラム レンダー距離

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

人事 visual システムには、fixates し、オブジェクトについて重点的に複数の距離に依存する信号が統合されています。
* [宿泊施設](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)-個々 の目のフォーカスします。
* [収束](https://en.wikipedia.org/wiki/Convergence_(eye))- 移動内側または外側のオブジェクトの中心に 2 つ目です。
* [双眼鏡ビジョン](https://en.wikipedia.org/wiki/Stereopsis)-左と右目イメージ オブジェクトの距離、固定のポイントから離れた場所に依存している間の不一致です。
* 網掛け、相対的な angular サイズ、およびその他の装置は単眼式 (1 つ目) キュー。

収束と宿泊施設は網膜超のキューに関連するさまざまな距離でオブジェクトを認識し、目を変更する方法であるため一意です。 自然な表示は、収束および宿泊施設はリンクされます。 目を表示 (例:、鼻) ほぼ何かと、見た目の良いクロス near ポイントに対応します。 目表示と何か無限大目が並列になると、目では、無限に対応しています。 HoloLens ソックスを着けずにユーザーは、2.0 m 鮮明な画像は、HoloLens に表示されるため、光学距離約 2.0 m ユーザーから離れた場所に固定は維持するために常に可能になります。 アプリ開発者のコントロールはコンテンツとホログラムをさまざまな深さで配置することでユーザーの目が収束できます。 ユーザーは、対応するし、さまざまな距離に収束、2 つのキューの間の自然なリンクが破損していると、競合の規模が大きい場合に特に visual 不安または疲労、する可能性です。 Vergence 宿泊施設競合から不安を回避またはユーザーができるだけ 2.0 m の近くに収束するコンテンツを保持することで最小限に抑えることができます (つまり、シーンの深さの多くで配置可能な場合は、2.0 m の近くの関心のある領域)。 コンテンツを配置することはできませんとさまざまな距離の間、ユーザーは視線 's ときに、vergence accomodation 競合からほぼ 2.0 m 不安には最大です。 つまり、静止ホログラム 50 cm を使用してもホログラム 50 cm すぐに参照を維持する時間の経過と共に、奥に向かってを移動するで検索する快適です。

この距離で完全に重複する 2 つのディスプレイが設計されているために、2.0 m にコンテンツを配置することが得策ですも。 この面に配置されたイメージ、holographic のフレームの端に動かすから消え、別の可視ながら 1 つの表示。 この双眼鏡いろいろとをホログラムの深さに対する認識に悪影響を与えることができます。

**ユーザーからホログラムを配置するための最適な距離**

![ユーザーからホログラムを配置するための最適な距離](images/distanceguiderendering-750px.png)

**クリップ平面**快適性を最大 1 m で始まるコンテンツの fadeout と 85 cm にクリッピング レンダー距離お勧めします。 ホログラムとユーザーが両方の静止ホログラムのアプリケーションを表示できる快適に近い 50 cm として。 その場合、アプリケーションが 30 cm とのクリップの平面を配置する必要があり、フェードアウトは少なくとも 10 cm クリップ平面からを起動する必要があります。 コンテンツはユーザーは、近くまたはホログラムから移動頻繁またはことホログラムは頻繁に近い場所に移動するか、ユーザーからこのような状況はから不安が発生する可能性が高いことを確認することが重要 85 cm よりも近いたびに、vergence 宿泊施設競合しています。 85 cm コンテンツは、85 cm 開発者にとって適切な目安は、場所のユーザーやホログラム移動しない t の 25% を超える深さにシナリオを設計するよりも近いレンダリングする必要がある。 ときに、ユーザーからより近くの対話の必要性を最小限に抑えるコンテンツを設計する必要があります。彼の時間。

**ベスト プラクティス**ホログラムを配置するための最適なゾーンが 1.25 m と 5 分間はホログラムが 2 m に配置されることはできず、収束と宿泊施設間の競合を回避することはできません、します。 すべてのケースでは、デザイナーがコンテンツを 1 以上の対話をユーザーに促すことを構成する必要がありますメートル離れた場所 (例: コンテンツのサイズを調整して、既定の配置パラメーター)。

## <a name="stabilization-plane"></a>安定化プレーン
> [!NOTE]
> デスクトップのイマーシブ ヘッドセットの安定化平面の設定は通常悪化ピクセルあたりの深さに基づく reprojection を有効にするシステムに、アプリの深度バッファーを提供するよりも低い画質を提供しています。 で、HoloLens を実行していない限り安定化平面の設定を一般に避ける必要があります。

HoloLens では、ハードウェア依存の holographic 安定の高度な手法を実行します。 これは主に自動であり、モーション センサーと見た (CameraPose) の変更を行う、シーンをアニメーション化して、ユーザーが自分の頭に移動する必要があります。 この安定化を最大化するには、安定化平面と呼ばれる、1 つの平面が選択されます。 シーン内のすべてのホログラムがいくつかの安定化を受信中に安定化平面にホログラムはハードウェアの最大の安定化を受信します。

![3D オブジェクトの平面を安定化](images/stab-plane-500px.jpg)

デバイスは、この平面の選択は自動的に試行しますが、アプリケーションは、シーン内のフォーカス ポイントを選択してこの処理に利用できます。 最適ながポイントしてシーンを集中し、これに渡す、HoloLens で実行されている unity アプリを選択する必要があります[SetFocusPoint()](focus-point-in-unity.md)します。 DirectX のフォーカス ポイントを設定する例は、既定の回転キューブ テンプレートに含まれます。

Unity アプリをデスクトップ PC に接続されている、イマーシブ ヘッドセットを実行すると Unity によって、Windows アプリによって明示的な作業なしのより高いイメージ品質を提供する、通常はピクセルあたりの reprojection を有効にするには、深度バッファー送信に注意してください。 ピクセルあたりの reprojection を上書きする、フォーカス ポイントを提供する場合ようにする必要がありますのみ行うこと、HoloLens でアプリが実行されている場合。




```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

フォーカス ポイントの配置の条件によって大きく変わりますホログラムを探しています。 アプリは参照の視線入力ベクトルを備え、アプリ デザイナーが、ユーザーを観察するどのようなコンテンツを認識します。

開発者ホログラムを安定化するためにできる単一の最も重要な点は、60 FPS で表示するためには。 60 FPS の下のドロップはホログラム安定性、安定化平面の最適化に関係なくを大幅に削減されます。

**ベスト プラクティス**安定化平面を設定する汎用の方法はありませんし、アプリに固有であるため、メインの推奨事項は、自分のシナリオに最適に動作を確認します。 ただし、この平面上のすべてのコンテンツが完全に安定しているために、できるだけ多くのコンテンツを含む、安定化プレーンを配置するしてみてください。

次に、例を示します。
* コンテンツのあるコンテンツがある場合のみ平面 (アプリの読み取り、ビデオの再生アプリ) 平面と安定化平面を揃えます。
* 世界ロックは 3 つの小さい球体がある場合は、すべての球体の中心を現在には、ユーザーのビュー [切り取り]、安定化プレーンを確認します。
* シーンでは、本質的に異なる深さでコンテンツがない場合は、オブジェクトで優先さらにします。
* ホログラム ユーザーと一致するすべてのフレームを見て、安定化ポイントを調整することを確認します。

**回避すべき点**安定化平面は優れた場合は誤用するが、安定したホログラムを実現するためのツールは、重大なイメージが不安定になることができます。
* なる可能性があるため、安定化が、ユーザーの背後にあるプレーンまたはユーザーのビューになっているオブジェクトにアタッチされているは「ファイア アンド フォーゲット」をしません。 通常の安定化平面は反対のカメラ転送 (例: camera.forward) に設定されていることを確認します。
* 両極端の間を行き来安定化平面を迅速に変更しないでください。
* 安定化平面距離固定向きに設定のままにしないでください。
* 安定化平面を切り抜けるには、ユーザーは思わないでください。
* 代わりにピクセルあたりの深さに基づく reprojection を利用して、HoloLens ではなく、PC、デスクトップで実行されているときに、フォーカス ポイントを設定しないでください。

## <a name="color-separation"></a>色の分離 

HoloLens のディスプレイの性質上、「色分離」と呼ばれる成果物を考えられる可能性が場合があります。 個々 の基本色の赤、緑、青に複数の分割イメージとしてマニフェストします。 成果物は、大量の赤、緑、および青があるために、白のオブジェクトを表示するときに特に表示できます。 ユーザー ホログラムを視覚的に追跡するときに最もと発音を高速で holographic フレーム間で移動です。 成果物がマニフェストは別の方法では、オブジェクトを歪める/変形です。 オブジェクトがハイ コントラストまたは純粋な色 (赤、緑、青) 色分離がオブジェクトのさまざまな部分を歪めるとして認識します。

**ユーザーが自分の頭の辺を回転としてようヘッド ロック白い round カーソルのどのような色分離の例になります。**

![ユーザー側に自分の頭を回転するようようヘッド ロック白い round カーソルのどのような色分離の例になります。](images/colorseparationofroundwhitecursor-300px.png)

色の分離を完全に回避するために困難ですが、それを軽減するために使用できるいくつかの手法があります。

**色分離で確認できます。**
* Head ロック オブジェクトをなどにすばやく、移動、オブジェクト、[カーソル](cursors.md)します。
* オブジェクトから遠実質的には、[安定化平面](hologram-stability.md#stabilization-plane)。

**分離の色の効果を減衰させます。**
* ユーザーの視線の先を後退させるオブジェクトを作成します。 いくつかの慣性を持ち、"スプリング"で、視線の先に接続されている場合と表示されます。 これは、(分離距離を減らす) カーソルの速度が低下し、ユーザーの可能性が高い視線入力ポイントの背後に配置します。 ユーザーが自分の視線をシフトを停止するときに迅速にキャッチ限り、非常に自然な感覚します。
* ホログラムを移動する場合は、ユーザーが自分以外でそれに続くが予想される場合の移動速度 5 度/秒以下をお試しください。
* 使用*light*の代わりに*geometry*カーソル。 視線の先に接続されている仮想の照明のソースは、対話型のポインターとして認識されますが、色分離は発生しません。
* ユーザーに gazing ホログラムを一致するように、安定化プレーンを調整します。
* オブジェクトの赤、緑、青を作成します。
* ぼかしのバージョンのコンテンツに切り替えます。 たとえば、round 白いカーソルでは、モーションの方向の向きが若干ぼかした行への変更可能性があります。

として、前に 60 FPS でレンダリングと安定化平面の設定はホログラム安定性のための最も重要な手法です。 顕著な色の分離、直面している場合、フレーム レートが期待を満たしていることを最初にします。

## <a name="see-also"></a>関連項目
* [複合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)
* [色、ライト、マテリアル](color,-light-and-materials.md)
* [相互作用の基礎](interaction-fundamentals.md)