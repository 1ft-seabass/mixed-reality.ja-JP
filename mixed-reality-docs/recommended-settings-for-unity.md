---
title: Unity の推奨設定
description: Unity には、プロジェクトの設定によって切り替えることができる mixed reality に固有のいくつかの動作が用意されています。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: unity、設定、mixed reality
ms.openlocfilehash: 2ab7eb0f9a7e06506ef8c57103518d8ef0a775df
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597635"
---
# <a name="recommended-settings-for-unity"></a>Unity の推奨設定

Unity には、すべてのプラットフォームの平均ケースである既定のオプションのセットが用意されています。 ただし、Unity は、プロジェクト設定を通じて切り替えることができる mixed reality に固有のいくつかの動作を提供します。

## <a name="performant-environment-set-up"></a>パフォーマンスに優れた環境のセットアップ

### <a name="low-quality-settings"></a>低品質の設定

環境の**Unity 品質設定**を**非常に低い**ものに変更することが重要です。 これにより、アプリケーションが適切なフレームレートで実行されるようにすることができます。 これは、HoloLens 開発で非常に重要です。 イマーシブヘッドセットでの開発では、VR エクスペリエンスを実現するデスクトップの仕様によっては、より低い品質パラメーターを使用せずにフレームレートを達成できます。

Unity 2018 LTS + では、プロジェクトの品質レベルは次の方法で設定できます。

[**プロジェクト設定**の**編集** > プロジェクトの設定] の [**品質**の > ] で、[**低**品質レベル] の下矢印をクリックして**既定値**を設定 > ます。

### <a name="lighting-settings"></a>光源の設定

品質のシーン設定と同様に、混合の現実アプリケーションに最適な光源設定を設定することが重要です。 Unity では、通常、シーンのパフォーマンスに最大の影響を与える光源の設定は、**リアルタイムのグローバルな照明**です。 これをオフにするには、 **[ウィンドウ]** の下に移動し、 > **光源の設定** > **リアルタイムのグローバル照明**で**表示** > ます。

他にも光源の設定があり**ます。** この設定により、イマーシブヘッドセットに対して高性能で視覚的な結果を得ることができますが、通常は HoloLens 開発には適用されません。 **焼き込みグローバル Illumniation**は、不明な環境と変化する環境の性質のために、通常 HoloLens では検出されない静的なオブジェクトに対してのみ計算されます。

詳細については、 [Unity からのグローバルな照明](https://docs.unity3d.com/Manual/GIIntro.html)をお読みください。 

>[!NOTE]
> **リアルタイムグローバル照明**は**シーンごと**に設定されるため、開発者はプロジェクト内のすべての Unity シーンに対してこのプロパティを保存する必要があります。

### <a name="single-pass-instancing-rendering-path"></a>シングルパスインスタンスレンダリングパス

混合現実アプリケーションでは、シーンはユーザーに対して1回ずつ、2回表示されます。 従来の3D 開発と比較すると、これにより、計算する必要がある作業量が実質的に倍になります。 したがって、CPU と GPU 時間の両方を保存するには、Unity で最も効率的なレンダリングパスを選択することが重要です。 シングルパスインスタンスレンダリングでは、Mixed Reality アプリ用の Unity レンダリングパイプラインが最適化されます。そのため、すべてのプロジェクトに対してこの設定を既定で有効にすることをお勧めします。

Unity プロジェクトでこの機能を有効にするには

1)  **プレーヤーの XR の設定**を開きます ( **[編集]**  > **プロジェクトの設定** > **player** > **XR 設定**)
2) **[ステレオレンダリングメソッド]** ドロップダウンメニューから **[シングルパスインスタンス]** を選択します ( **[Virtual Reality がサポートさ]** れる チェックボックスをオンにする必要があります)

この表示方法の詳細については、Unity から次の記事をお読みください。

- [高度なステレオレンダリングを使用して AR と VR のパフォーマンスを最大化する方法](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [シングルパスのインスタンス化](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> 単一パスのインスタンス化に関する一般的な問題の1つは、開発者が既にインスタンス化用に作成されていない既存のカスタムシェーダーを持っている場合です。 この機能を有効にした後、開発者は、一部のオブジェクトが1つの目にしか表示されないことに気付く場合があります。 これは、関連付けられたカスタムシェーダーに、インスタンス化するための適切なプロパティがないためです。
>
> この問題への対処方法については、Unity[の HoloLens のシングルパスステレオレンダリング](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)に関する説明を参照してください。

### <a name="enable-depth-buffer-sharing"></a>深度バッファーの共有を有効にする

ユーザーの認識によってより適切なホログラムの安定性を実現するには、Unity で**深度バッファー共有**プロパティを有効にすることをお勧めします。 これをオンにすると、Unity は、アプリケーションによって生成された深度マップを Windows Mixed Reality プラットフォームと共有します。 これにより、プラットフォームは、アプリケーションによってレンダリングされる特定のフレームに対して、シーン専用のホログラムの安定性を向上させることができます。

Unity プロジェクトでこの機能を有効にするには

1) **プレーヤーの XR の設定**を開きます ( **[編集]**  > **プロジェクトの設定** > **player** > **XR 設定**)
2) [**仮想現実の sdk**で**深度バッファーの共有を有効にする**] のチェックボックスをオンにして、[ **Windows Mixed reality**の拡張 > ます (仮想環境の**サポート**チェックボックスをオンにする必要があります)]

また、特に HoloLens 開発の場合は、このパネルの **[深度書式]** の下にある**16 ビット深度**を選択することをお勧めします。 16ビットを24ビットに比較すると、帯域幅の要件を大幅に削減できます。これにより、移動または処理する必要があるデータの量が少なくなります。

Windows Mixed Reality プラットフォームがホログラムの安定性を最適化するためには、深度バッファーが正確であり、画面上のレンダリングされたホログラムに一致することに依存します。 したがって、で深度バッファーを共有する場合は、色をレンダリングするときに、深度も表示することが重要です。 Unity では、ほとんどの不透明または TransparentCutout のマテリアルが既定で深度をレンダリングしますが、透明なテキストオブジェクトは通常、深度をレンダリングしません。ただし、これはシェーダーに依存します。

[Mixed Reality Toolkit 標準シェーダー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)を使用する場合、透過オブジェクトの深度をレンダリングするには、次のようにします。

1) MRTK Standard シェーダーを使用している透明な素材を選択し、[インスペクターエディター] ウィンドウを開きます。
2) 深度バッファーの共有 警告で **今すぐ修正** ボタンを選択します。 これは、**表示モード**を**カスタム**に設定することによって、手動でも実行できます。次に、 **[モード]** を **[透明]** に設定し、最後に **[深度書き込み]** を**オン**に設定します。

> [!IMPORTANT]
> これらの値をカメラの近距離/遠方の設定と共に変更する場合、開発者は Z 戦いに注意する必要があります。 Z 戦いは、2つのオブジェクトが同じピクセルにレンダリングしようとしたときに、深度バッファーの忠実性が制限されていることが原因で発生します ( z 深度) では、他のオブジェクトの前面にあるオブジェクトを識別できません。 開発者は、2つのゲームオブジェクトが同じ z 深度値に対して*戦う*ので、ちらつきがあることに注意してください。 これは、カメラからの z 深度に対して計算する各オブジェクトの値の範囲が大きくなるため、24ビットの深度形式に切り替えることによって解決できます。
>
> ただし、特に HoloLens 開発では、カメラの近距離および遠くの平面をより小さな範囲に変更し、16ビット深度形式を保持することをお勧めします。 Z 深度は、近距離および遠くのカメラ面に沿った値の範囲に非直線的にマップされます。 これは、シーンの*メインカメラ*を選択し、**インスペクター** の下の **近距離 & 遠くのクリッププレーン**の値を変更して範囲を小さくすることで変更できます (つまり、 1000 m から100m または他の x 値など)

>[!IMPORTANT]
> 16ビット深度形式を使用する場合[、Unity はステンシルバッファーを作成しません](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)。 そのため、一部の Unity UI 効果とその他のステンシルが必要な効果は、8ビットの[ステンシルバッファー](https://docs.unity3d.com/Manual/SL-Stencil.html)を作成する24ビットの深度形式を選択しない限り機能しません。

### <a name="building-for-il2cpp"></a>IL2CPP 向けのビルド

Unity では .NET scripting バックエンドのサポートが非推奨とされているため、開発者はその UWP visual studio ビルドに対して**IL2CPP**を利用することをお勧めします。 これにはさまざまな利点がありますが、Unity の**Il2CPP**から visual studio ソリューションをビルドすることは、従来の .net 方式よりも大幅に遅くなる可能性があります。 そのため、開発の反復時間に保存する**IL2CPP**を構築するためのベストプラクティスに従うことを強くお勧めします。

1) 毎回同じディレクトリにプロジェクトをビルドして、インクリメンタルビルドを活用し、ビルド済みのファイルを再利用します。
2) プロジェクト & ビルドフォルダーに対するマルウェア対策ソフトウェアスキャンを無効にする
   - Windows 10 設定アプリで**ウイルス & 脅威保護**を開く
   - **[ウイルス & 脅威保護の設定]** の下の **[設定の管理]** を選択します。
   - **[除外]** セクションで **[除外の追加または削除]** を選択します。
   - **[除外の追加]** をクリックし、Unity プロジェクトコードとビルド出力を含むフォルダーを選択します。
3) SSD を使用してビルドする

詳細については、「 [IL2CPP のビルド時間の最適化](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)」を参照してください。

> [!NOTE]
> 特に、大きなアセット (スクリプト ファイルを除く) がある場合や、常にシーンやアセットを変更する Unity プロジェクトの場合は、[キャッシュ サーバー](https://docs.unity3d.com/Manual/CacheServer.html)をセットアップするとよいでしょう。 プロジェクトを開く際に、Unity は条件を満たすアセットを内部キャッシュ フォーマットで開発者のコンピューターに格納します。 項目を変更した場合は、再インポートして再処理されるようにする必要があります。 このプロセスが 1 回実行されると、キャッシュ サーバーに保存され、すべての開発者に共有されます。すべての開発者がローカルで新しい変更の再インポート処理を行う必要がなくなるので、時間を節約できます。

## <a name="publishing-properties"></a>発行のプロパティ

### <a name="holographic-splash-screen"></a>Holographic スプラッシュスクリーン

HoloLens には、モバイルクラスの CPU と GPU が搭載されています。これは、アプリの読み込みに少し時間がかかる場合があることを意味します。 アプリが読み込まれている間、ユーザーには黒が表示されるので、何が起こっているかがわかります。 読み込み中に知らせるためするには、holographic スプラッシュスクリーンを追加します。

Holographic スプラッシュスクリーンを切り替えるには、次のようにします。

1) [ **Edit** > **Project Settings** > **Player** ] ページにアクセスします
2) **[Windows ストア]** タブをクリックし、 **[スプラッシュイメージ]** セクションを開きます。
3) 必要なイメージを**Windows Holographic > Holographic スプラッシュイメージ**プロパティの下に適用します。
    - [ **Unity スプラッシュスクリーンを表示**する] オプションを切り替えると、unity ブランド化されたスプラッシュスクリーンが有効または無効になります。 Unity Pro ライセンスを持っていない場合は、Unity ブランド化されたスプラッシュスクリーンが常に表示されます。
    - **Holographic スプラッシュイメージ**が適用されている場合は、[Unity スプラッシュスクリーンを表示する] チェックボックスが有効になっているか無効になっているかに関係なく、常に表示されます。 カスタム holographic スプラッシュイメージの指定は、Unity Pro ライセンスを持つ開発者のみが使用できます。

|  Unity スプラッシュスクリーンを表示する  |  Holographic スプラッシュイメージ  |  動作 |
|----------|----------|----------|
|  On  |  None  |  既定の Unity スプラッシュスクリーンを5秒間、またはアプリが読み込まれるまでのいずれか長い方に表示します。 |
|  On  |  カスタム  |  5秒間、またはアプリが読み込まれるまでのいずれか長い方のカスタムスプラッシュスクリーンを表示します。 |
|  [オフ]  |  None  |  アプリが読み込まれるまで、透明な黒 (何も表示されません) を表示します。 |
|  [オフ]  |  カスタム  |  5秒間、またはアプリが読み込まれるまでのいずれか長い方のカスタムスプラッシュスクリーンを表示します。 |

詳細については、 [Unity のスプラッシュスクリーンのドキュメント](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html)を参照してください。

### <a name="tracking-loss"></a>損失の追跡

Mixed reality ヘッドセットは、その周囲に環境が表示されているかどうかに依存します。これに[より、ホログラム](coordinate-systems-in-unity.md)を位置どおりに保つことができます。 ヘッドセットが世界中で見つからない場合、ヘッドセットは*追跡が失わ*れていると言います。 このような場合、空間ステージ、空間アンカー、空間マッピングなど、世界的にロックされている座標系に依存する機能は機能しません。

追跡の停止が発生した場合、Unity の既定の動作では、ホログラムのレンダリングを停止し、[ゲームのループ](https://docs.unity3d.com/Manual/ExecutionOrder.html)を一時停止して、ユーザーにとって簡単にフォローしている追跡紛失通知を表示します。 カスタム通知は、追跡損失イメージの形式で指定することもできます。 エクスペリエンス全体の追跡に依存するアプリの場合は、追跡が回復されるまで Unity がこの処理を完全に処理できるようにするだけで十分です。 開発者は、追跡の停止中に表示されるカスタムイメージを指定できます。

失われた画像の追跡をカスタマイズするには:

1) [ **Edit** > **Project Settings** > **Player** ] ページにアクセスします
2) **[Windows ストア]** タブをクリックし、 **[スプラッシュイメージ]** セクションを開きます。
3) **[Windows Holographic > Tracking 損失イメージ]** プロパティで目的のイメージを適用します。

#### <a name="opt-out-of-automatic-pause"></a>自動一時停止のオプトアウト

一部のアプリでは、追跡を必要としない場合があります (たとえば、360度のビデオビューアーなどの[向き専用のアプリ](coordinate-systems-in-unity.md))。追跡が失われても、処理を中断せずに処理を継続する必要がある場合があります。 このような場合、アプリは、既定では追跡動作の損失をオプトアウトできます。 これを選択する開発者は、追跡損失のシナリオで適切に表示されないオブジェクトを表示/無効にする役割を担います。 ほとんどの場合、この場合に表示することをお勧めするコンテンツは、本文ロックされたコンテンツのみで、メインカメラを中心にしています。

自動一時停止動作を無効にするには、次のようにします。

1)  > **プロジェクト設定**の**編集** ページにアクセスして > **プレーヤー**  ページ
2) **[Windows ストア]** タブをクリックし、 **[スプラッシュイメージ]** セクションを開きます。
3) Windows Holographic > を変更します。 **[一時停止の追跡を停止してイメージを表示**] チェックボックスをオンにします。

#### <a name="tracking-loss-events"></a>損失イベントの追跡

追跡が失われたときのカスタム動作を定義するには、グローバル[追跡損失イベント](tracking-loss-in-unity.md)を処理します。

### <a name="capabilities"></a>機能

アプリで特定の機能を利用するには、マニフェストで適切な機能を宣言する必要があります。 マニフェスト宣言は Unity で作成できるため、後続のすべてのプロジェクトエクスポートに含まれます。

次の方法で、Mixed Reality アプリケーションに対して機能を有効にすることができます。

1) [ **Edit** > **Project Settings** > **Player** ] ページにアクセスします
2) **[Windows ストア]** タブをクリックし、 **[発行の設定]** セクションを開いて、**機能**の一覧を探します。

Holographic アプリで一般的に使用される Api を有効にするための適用可能な機能は次のとおりです。
<br>

|  機能  |  機能を必要とする Api |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  WebCam  |  PhotoCapture と VideoCapture |
|  PicturesLibrary / VideosLibrary  |  PhotoCapture または VideoCapture (キャプチャされたコンテンツを格納する場合) |
|  マイク  |  VideoCapture (オーディオをキャプチャする場合)、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (および Unity Profiler の使用) |

## <a name="see-also"></a>「

* [Unity 開発の概要](unity-development-overview.md)
* [Mixed Reality のパフォーマンスを理解する](understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
