---
title: MR 250 - HoloLens とイマーシブ ヘッドセットの共有
description: このコーディング ホログラム複合現実デバイス間の共有の詳細については、Unity、Visual Studio、HoloLens、および Windows Mixed Reality ヘッドセットを使用してチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity のイマーシブなアニメーション コント ローラー、共有、xbox コント ローラー、ネットワーク、クロス デバイス
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598044"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR が 250 の共有:HoloLens とイマーシブ ヘッドセット

柔軟性のユニバーサル Windows プラットフォーム (UWP) により、複数のデバイスにまたがるアプリケーションを作成する簡単です。 この柔軟性により、各デバイスの長所を活用するエクスペリエンスを生み出すことができます。 このチュートリアルでは、イマーシブ ヘッドセットを HoloLens と Windows Mixed Reality の両方で実行されている基本の共有エクスペリエンスを説明します。 このコンテンツは、Microsoft Build 2017 カンファレンス、ワシントン州シアトルで配信元でした。

**このチュートリアルでご紹介します。**

* UNET を使用してネットワークをセットアップします。
* 複合現実デバイス間でホログラムを共有します。
* 複合現実デバイスが使用されているに応じてアプリケーションの別のビューを確立します。
* HoloLens のユーザーがいくつかの簡単なパズルを使用してイマーシブ ヘッドセット ユーザーをガイドする共有エクスペリエンスを作成します。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR が 250 の共有:HoloLens とイマーシブ ヘッドセット</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* Windows 10 PC で、[ために必要な開発ツール](install-the-tools.md)と[Windows Mixed Reality イマーシブ ヘッドセットをサポートするように構成](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)します。
* お使いの PC で動作する Xbox コント ローラー。
* 少なくとも 1 つの HoloLens デバイスは、1 つのイマーシブ ヘッドセット。
* 探索の UDP ブロードキャストを許可するネットワーク。

### <a name="project-files"></a>プロジェクト ファイル

* ダウンロード、[ファイル](https://github.com/Microsoft/MixedReality250/archive/master.zip)プロジェクトに必要です。 覚えやすい場所にファイルを抽出します。
* このプロジェクトで必要な[Windows Mixed Reality サポートで推奨されるバージョンの Unity](install-the-tools.md)します。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/MixedReality250)します。

## <a name="chapter-1---holo-world"></a>第 1 章 - Holo 世界

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>目標

開発環境が単純なプロジェクトに対応することを確認します。

### <a name="what-we-will-build"></a>構築します。

HoloLens と Windows Mixed Reality ヘッドセット没入型のいずれかでホログラムを表示するアプリケーション。

### <a name="steps"></a>手順
* Unity を開きます。
    * **[開く]** を選択します。
    * プロジェクト ファイルを抽出した場所に移動します。
    * **[フォルダーの選択]** をクリックします。
    * *少し、初めてのプロジェクトを処理する Unity の中にかかります。*
* Unity で Mixed Reality が有効になっていることを確認します。
    * ビルドの設定 ダイアログを開きます (**コントロール + Shift + B**または**ファイル > Build Settings...**).
    * 選択**ユニバーサル Windows プラットフォーム**クリックして**スイッチ プラットフォーム**します。
    * 選択**編集 > プレーヤー設定**します。
    * **インスペクター** 、右側にパネルで、展開**XR 設定**します。
    * チェック、**仮想現実サポート**ボックス。
    * *Windows Mixed Reality 仮想現実 SDK があります。*
* シーンを作成します。
    * **階層**を右クリックして**Main Camera**選択**削除**します。
    * **HoloToolkit > の入力 > プレハブ**ドラッグ**MixedRealityCameraParent**を**階層**します。
* ホログラムをシーンに追加します。
    * **AppPrefabs**ドラッグ**スカイ ボックス**を**シーン ビュー**します。
    * **AppPrefabs**ドラッグ**マネージャー**を**階層**します。
    * **AppPrefabs**ドラッグ**島**を**階層**します。
* 保存し、ビルド
    * 保存 (か**コントロール + S**または**ファイル > シーンを保存**)
    * これは、新しいシーンであるために名前を付ける必要があります。 名前は関係ありませんが、SharedMixedReality を使用します。
* Visual Studio へのエクスポートします。
    * [ビルド] メニューを開きます (**コントロール + Shift + B**または**ファイル > Build Settings**)
    * クリックして**開くシーンを追加します。**
    * 確認**UnityC#プロジェクト**
    * **[Build]** をクリックします。
    * ファイル エクスプ ローラー ウィンドウが表示されますでという名前の新しいフォルダーを作成**アプリ**します。
    * 1 回のクリック、**アプリ**フォルダー。
    * キーを押して**フォルダーを選択します。**
    * **ビルドが完了するまで待ちます**
    * ファイル エクスプ ローラー ウィンドウが表示されますに移動します、**アプリ**フォルダー。
    * ダブルクリック**SharedMixedReality.sln** Visual Studio を起動するには
* Visual Studio からビルドします。
    * ターゲットを上部のツールバーを使用して変更**リリース**と**x86**します。
    * 矢印をクリックして**ローカル マシン**選択と**デバイス**HoloLens にデプロイするには
    * 矢印をクリックして**デバイス**選択**ローカル マシン**mixed reality ヘッドセットをデプロイします。
    * クリックして**デバッグ]、[デバッグなしで開始**または**コントロール + f5 キーを押して**アプリケーションを起動します。

### <a name="digging-into-the-code"></a>コードをについてください。

[プロジェクト] パネルに移動します**Assets\HoloToolkit\Input\Scripts\Utilities**をダブルクリックして**MixedRealityCameraManager.cs**を開きます。

**概要:** MixedRealityCameraManager.cs は、デバイスに基づいて、品質のレベルとバック グラウンドの設定を調整する単純なスクリプトです。 キー HolographicSettings.IsDisplayOpaque、これにより、デバイスが、HoloLens を検出するスクリプトを次に示します (IsDisplayOpaque false を返す) または (IsDisplayOpaque true を返す)、イマーシブ ヘッドセット。

### <a name="enjoy-your-progress"></a>進行状況をお楽しみください。

この時点で、アプリケーションはホログラムだけを表示します。 後で、ホログラムに相互作用を追加します。 両方のデバイスは、レンダリング、ホログラム同じ。 イマーシブ ヘッドセットは青色空とクラウドのバック グラウンドにも表示します。

## <a name="chapter-2---interaction"></a>第 2 章 – 相互作用

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>目標

Windows Mixed Reality アプリケーションの入力を処理する方法を示します。

### <a name="what-we-will-build"></a>構築します。

第 1 章からアプリケーションを構築して、ユーザーが、ホログラムを選択し、HoloLens で現実世界の画面で、または、イマーシブ ヘッドセットの仮想テーブルに配置できるようにする機能を追加します。

**入力リフレッシャーは:** HoloLens 選択ジェスチャは、**エア タップ**します。 イマーシブ ヘッドセットでの使用、 **A** Xbox コント ローラー上のボタンをクリックします。 入力の詳細については[ここから始めて](gestures.md)します。

### <a name="steps"></a>手順
* 入力マネージャーを追加します。
    * **HoloToolkit > の入力 > プレハブ**ドラッグ**InputManager**に**階層**の子として**マネージャー**します。
    * **HoloToolkit > の入力 > プレハブ > カーソル**ドラッグ**カーソル**に**階層**します。
* 空間マッピングを追加します。
    * **HoloToolkit > SpatialMapping > プレハブ**ドラッグ**SpatialMapping**に**階層**します。
* 仮想 Playspace を追加します。
    * **階層**展開**MixedRealityCameraParent**選択**境界**
    * **インスペクター**パネルのチェック ボックスを有効にするを**境界**
    * **AppPrefabs**ドラッグ**VRRoom**に**階層**します。
* WorldAnchorManager を追加します。
    * **階層**、**マネージャー**します。
    * **インスペクター**、 をクリックして**コンポーネントの追加**します。
    * 型**World アンカー Manager**します。
    * 選択**World アンカー Manager**に追加します。
* TapToPlace を島に追加します。
    * **階層**、展開**島**します。
    * 選択**MixedRealityLand**します。
    * **インスペクター**、 をクリックして**コンポーネントの追加**します。
    * 型**の場所をタップして**して選択します。
    * 確認**Tap に親を配置**します。
    * 設定**配置オフセット**に **(0, 0.1, 0)** します。
* 保存し、以前とビルド

### <a name="digging-into-the-code"></a>コードをについてください。

**スクリプト 1 - GamepadInput.cs**

[プロジェクト] パネルに移動します**Assets\HoloToolkit\Input\Scripts\InputSources**をダブルクリックして**GamepadInput.cs**を開きます。 [プロジェクト] パネルで同じパスにもダブルクリック**InteractionSourceInputSource.cs**します。

両方のスクリプトが共通の基本クラス BaseInputSource を持つことに注意してください。

BaseInputSource、InputManager では、により、スクリプトでイベントをトリガーへの参照を保持します。 この場合、InputClicked イベントが関連します。 これは、スクリプト 2、TapToPlace を取得する際に重要になります。 GamePadInput の場合は、A ボタンを押す、コント ローラーでのポーリングし、InputClicked イベントが発生しました。 InteractionSourceInputSource の場合は、TappedEvent への応答で InputClicked イベントを発生します。

**2 - TapToPlace.cs スクリプト**

[プロジェクト] パネルに移動します**Assets\HoloToolkit\SpatialMapping\Scripts**をダブルクリックして**TapToPlace.cs**を開きます。

まず、多くの開発者が Holographic アプリケーションを作成するときに実装するには、ジェスチャ入力ホログラムは移動です。 そのため、このスクリプトを十分にコメントするよう努めていますしました。 いくつかの点では、このチュートリアルでは注目すべきです。

まず、TapToPlace IInputClickHandler を実装することに注意してください。 IInputClickHandler は、GamePadInput.cs または InteractionSourceInputSource.cs によって発生する InputClicked イベントを処理する関数を公開します。 BaseInputSource TapToPlace のオブジェクトにフォーカスが中に、クリックを検出する OnInputClicked が呼び出されます。 HoloLens で airtapping または Xbox コント ローラーで、[A] ボタンを押してのいずれかは、イベントをトリガーします。

2 つ目は、参照テーブルのように、サーフェイス ゲーム オブジェクトを配置できるように、サーフェスがで参照されるかどうかの更新で、コードを実行します。 イマーシブ ヘッドセットは実際のサーフェスの概念をこれがないテーブルの一番上を表すオブジェクト (Vroom > TableThingy > キューブ) 更新プログラムでキャスト射線は仮想テーブルの上部と競合するので、SpatialMapping 物理層がマークされています。

### <a name="enjoy-your-progress"></a>進行状況をお楽しみください。

この時間に移動島を選択できます。 HoloLens の島を実際の画面に移動できます。 イマーシブ ヘッドセットには、仮想テーブルを追加しましたに島を移動できます。

## <a name="chapter-3---sharing"></a>第 3 章 - 共有

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>目標

ネットワークが正しく構成されていることを確認し、詳細空間アンカーは、デバイス間で共有される方法です。

### <a name="what-we-will-build"></a>構築します。

このプロジェクトはマルチプレイヤー プロジェクトに変換します。 ホストまたは結合のセッションに UI とロジックを追加します。 HoloLens のユーザーが互いを見るとクラウドのセッションで、頭の上、イマーシブ ヘッドセット ユーザーがクラウド アンカーが近くにあります。 イマーシブ ヘッドセット内のユーザーは、シーンの原点 HoloLens のユーザーに表示されます。 HoloLens のユーザーの同じ場所に島ホログラムがすべて参照してください。 キー、イマーシブ ヘッドセット内のユーザーがこの章では、中に、島にされませんが、アイランドの鳥アイ ビューで、HoloLens を非常によく似た動作をすることをお勧めします。

### <a name="steps"></a>手順
* 削除島と VRRoom
    * **階層**右**島**選択**削除**
    * **階層**右**VRRoom**選択**削除**
* Usland を追加します。
    * **AppPrefabs**ドラッグ**Usland**に**階層**します。
* **AppPrefabs**ドラッグするには、次の各**階層**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 保存し、以前とビルド

### <a name="digging-into-the-code"></a>コードをについてください。

[プロジェクト] パネルに移動します**Assets\AppPrefabs\Support\SharingWithUnet\Scripts**ダブルクリックして**UnetAnchorManager.cs**します。 デバイスの両方で同じスペースを共有できるように、別の HoloLens と追跡情報を共有する 1 つの HoloLens の機能は、魔法の近くです。 複合現実の電源がアライブの場合は、2 つ、またはより多くの人が同じデジタル データを使用して共同作業できます。

このスクリプトで指摘していくつかの点。

Start 関数のチェックに注意してください。 **IsDisplayOpaque**します。 この場合、アンカーが確立されている見かけ上します。 これは、イマーシブ ヘッドセットはインポートまたはアンカーをエクスポートする方法を公開しないためにです。 私たちは、HoloLens で実行している場合、ただし、このスクリプトはデバイス間で共有のアンカーを実装します。 セッションを開始するデバイスでは、エクスポートするためのアンカーを作成します。 セッションを開始したデバイスからは、セッションに参加するデバイスは、アンカーを要求します。

**エクスポートするには。**

ユーザーは、セッションを作成するときに、NetworkDiscoveryWithAnchors は UNETAnchorManagers CreateAnchor 関数を呼び出します。 CreateAnchor フローを追いかけてみましょう。

まず、前の基準の収集された可能性がありますがデータを消去する、いくつかのハウスキーピングを実行します。 キャッシュのアンカーを読み込むかどうかは確認します。 アンカーのデータは、キャッシュされた表現のアンカーを再利用で、ネットワーク経由で転送する必要。 データの量に保存できるようにの 5 ~ 20 mb にする傾向があります。 後で少し動作が表示されます。 アンカーを再利用しますが、場合でも、新しいクライアントを結合する場合にデータの準備がないアンカーのアンカーを取得する必要があります。

アンカーのデータの準備と言えば、WorldAnchorTransferBatch クラスは、アンカーのデータをインポートするには、別のデバイスまたはアプリケーションと機能に送信するためのアンカーのデータを準備するための機能を公開します。 エクスポート パスに対するだから私たち、WorldAnchorTransferBatch に、アンカーを追加し、ExportAsync 関数を呼び出します。 エクスポートのデータを生成し、ExportAsync は WriteBuffer コールバックを呼び出します。 すべてのデータがエクスポートされると ExportComplete が呼び出されます。 WriteBuffer では、エクスポートはあと保存リストにデータのチャンクを追加します。 ExportComplete で、配列にリストを変換します。 AnchorName 変数も設定されます、その他のデバイスを起動することがあるない場合、アンカーを要求します。

いくつかの場合、アンカーをエクスポートしませんまたはデータが少量は作成私たちはもう一度やり直してください。 ここでだけ呼び出して CreateAnchor もう一度です。

エクスポート パスに最終的な関数では、AnchorFoundRemotely です。 別のデバイスには、アンカーが検出されると、そのデバイスをホストに通知され、ホスト アンカーが「良いアンカー」シグナルとしてを使用してキャッシュできます。

**インポート。**

HoloLens は、セッションに参加する場合は、アンカーのインポートが必要です。 UNETAnchorManager の更新プログラムの関数で、AnchorName にポーリングされます。 アンカーの名前が変更されたときに、インポート プロセスを開始します。 まず、アンカーのローカル ストアから、指定した名前のアンカーを読み込むとします。 既にがある場合に、そのデータをもう一度ダウンロードしなくても使用できます。 これがなければ、ダウンロードを開始する WaitForAnchor を呼び出します。

ダウンロードが完了したら、NetworkTransmitter_dataReadyEvent が呼び出されます。 これは、ダウンロードされたデータで ImportAsync を呼び出すための更新ループでは通知します。 インポート処理が完了すると、ImportAsync は ImportComplete を呼び出します。 インポートが成功した場合は、アンカーは、プレーヤーのローカル ストアに保存されます。 により、PlayerController.cs は、実際には、ホストに適切なアンカーが確立されたことを認識させる AnchorFoundRemotely に呼び出しを行います。

### <a name="enjoy-your-progress"></a>進行状況をお楽しみください。

今回、HoloLens を持つユーザーをホストするセッションを使用して、**セッションを開始**UI のボタンをクリックします。 他のユーザー両方 HoloLens や、イマーシブ ヘッドセットは、セッションを選択し、選択、**セッションに参加する**UI のボタンをクリックします。 HoloLens デバイスで複数の人がある場合は、頭に赤のクラウドがあります。 ありますの各イマーシブ ヘッドセット、青色の雲が青色の雲とは、ヘッドセット上、ヘッドセットは HoloLens デバイスとして同じワールド座標空間を検索していないようです。

プロジェクトのこのポイントが含まれている共有アプリケーションです。非常にほとんど意味がありませんし、ベースラインとして機能する可能性があります。 [次へ] の章では、まず、ご利用いただくにユーザー エクスペリエンスを構築します。 共有のエクスペリエンスの設計に関するガイダンスを入手さらに、移動します。

## <a name="chapter-4---immersion-and-teleporting"></a>第 4 章 - Immersion と teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>目標

複合現実デバイスの種類ごとにエクスペリエンスを提供します。

### <a name="what-we-will-build"></a>構築します。

没入型の表示、南の島でイマーシブ ヘッドセット ユーザーを配置するアプリケーションを更新します。 HoloLens のユーザーには、アイランドのバード アイ ビューがあります。 各デバイスの種類のユーザーは、世界中に表示される他のユーザーを確認できます。 たとえば、HoloLens ユーザー島上の巨大なクラウドとして表示し、イマーシブ ヘッドセット ユーザーでは、島、上の他のパスに他のアバターがわかります。 イマーシブ ヘッドセット ユーザーは、HoloLens のユーザーが、島で探している場合にも、HoloLens のユーザーの視線の先光線のカーソルに表示されます。 HoloLens のユーザーは、各イマーシブ ヘッドセット ユーザーを表す島にアバターが表示されます。

**没入型のデバイスの更新の入力:**
* Xbox コント ローラーの左側のエンジンとエンジンの右ボタンが、プレーヤーを回転させる
* Xbox コント ローラーで、[Y] ボタンを保持しているが有効になります、[テレポート](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)カーソル。 カーソルが矢印インジケーターが回転 Y ボタンを離したときに、カーソルの場所に波及ができます。

### <a name="steps"></a>手順
* MixedRealityCameraParent MixedRealityTeleport に追加します。
    * **階層**、 **Usland**します。
    * **インスペクター**、有効にする**レベルの制御**します。
    * **階層**、 **MixedRealityCameraParent**します。
    * **インスペクター**、 をクリックして**コンポーネントの追加**します。
    * 型**Mixed Reality テレポート**して選択します。

### <a name="digging-into-the-code"></a>コードをについてください。

イマーシブ ヘッドセット ユーザーは、ケーブルで自分の Pc にテザリングされたされますが、アイランドは、ケーブルが長よりも大きい。 補正するために、ユーザーの動きとは無関係にカメラを移動できる必要があります。 参照してください、[元気の出るページ](comfort.md)複合現実のアプリケーションの (特に自己モーション センサーと locomotion) 設計の詳細についてはします。

このプロセスを説明するために 2 つの用語を定義すると便利ですがあります。 まず、**けん引**ユーザーからしないカメラを個別に移動するオブジェクトになります。 子ゲーム オブジェクト、**けん引**なります、**メイン カメラ**します。 メイン カメラは、ユーザーの頭にアタッチされます。

[プロジェクト] パネルに移動します**Assets\AppPrefabs\Support\Scripts\GameLogic**ダブルクリックして**MixedRealityTeleport.cs**します。

MixedRealityTeleport には、2 つのジョブがあります。 最初に、エンジンを使用して回転を処理します。 Update 関数で 'ButtonUp' LeftBumper と RightBumper のポーリングします。 GetButtonUp のみ true を返すボタンがアップ ダウンになった後は、最初のフレームでします。 わかった場合は、いずれかのボタンが発生し、ユーザーは、回転する必要があります。

私たちを回転フェードの操作を行います、フェード 'フェード コントロール' という名前の単純なスクリプトを使用しています。 これをユーザーが不安を招く可能性がある不自然の移動を確認するを防ぐために行います。 フェードとフェードアウト効果は非常に単純です。 ある分岐の前でブラック クアッド、**メイン カメラ**します。 フェードアウトとアルファ値は 0 から 1 に移行します。 これは、黒のピクセルをレンダリングし、それらの背後にある何かがわかりにくくなる 4 つの段階的にによりします。 フェードに戻るときに、アルファ値を 0 に移行します。

回転角度を計算します 回転していることに注意してください、**けん引**周りの回転角度を計算するが、**メイン カメラ**します。 これは、遠いとして重要、**メイン カメラ**0,0,0 から正確な少なく、けん引周りの回転角度になるユーザーの観点からは、します。 実際には、カメラの位置を回転しない場合、ユーザーは、円弧の周囲に移動は、**けん引**回転ではなく。

MixedRealityTeleport の 2 つ目のジョブは移動を処理するためには、**けん引**します。 これは、SetWorldPosition で行われます。 SetWorldPosition は必要なワールド位置を占めます。 したがって、percieve にユーザーが必要がある位置を受け取ります。 配置する必要があります、**けん引**マイナスのローカルの位置には、その位置にある、**メイン カメラ**、フレームごとに、そのオフセットが追加されます。

2 番目のスクリプトでは、SetWorldPosition を呼び出します。 そのスクリプトを見てみましょう。 [プロジェクト] パネルに移動します**Assets\AppPrefabs\Support\Scripts\GameLogic**ダブルクリックして**TeleportScript.cs**します。

このスクリプトは MixedRealityTeleport よりも少し複雑です。 スクリプトは、Y のボタン保持する Xbox コント ローラーを確認しています。 ボタンが保持されている間は、カーソルが表示されます、テレポート ダウンし、スクリプトが視線の先のユーザーの位置から伸びる射線をキャストします。 その光線が多いか少ないは画面と競合している場合は、上向き、画面は、テレポートに適切な画面に検討され、テレポート カーソル上でアニメーションが有効になります。 射線が多いか少ない上向きサーフェイスと衝突しない場合、カーソル上でアニメーションを無効化されます。 Y ボタンが解放され、光線の計算されるポイントは有効な位置をスクリプトは、射線が交差する位置を SetWorldPosition を呼び出します。

### <a name="enjoy-your-progress"></a>進行状況をお楽しみください。

この時間を友人を検索する必要があります。

もう一度、HoloLens を持つユーザーは、セッションをホストします。 他のユーザーはセッションに参加します。 アプリケーションには、最初の 3 つのユーザーに、島に 3 つのパスのいずれかで没入型のヘッドセットから参加が配置されます。 このセクションの島を探索してもかまいません。

詳細に注意してください:
1. HoloLens のユーザーを検索する方向を参照してください。 immersed のユーザーに役立ちますクラウド内の顔を確認できます。
2. 島アバターは、回転突き止めるがあります。 ユーザーが何に従うことはありません (その情報はありません) 実際には実際は、優れたエクスペリエンスのためです。
3. HoloLens のユーザーは、島を見て、immersed ユーザーにカーソルが表示されます。
4. HoloLens のユーザーを表すクラウドは、シャドウをキャストします。

## <a name="chapter-5---finale"></a>第 5 章「お

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>目標

2 つのデバイスの種類間のコラボレーション対話型環境を作成します。

### <a name="what-we-will-build"></a>構築します。

第 4 章に基づき島、パズルの近く、イマーシブ ヘッドセットを持つユーザーを取得すると、HoloLens ユーザーでは、パズルへの手掛かりのツールヒントが表示されます。 ロケット部屋にそのパズル過去と"準備完了"パッド上を取得のすべてのイマーシブ ヘッドセット ユーザー、ロケットが起動されます。

### <a name="steps"></a>手順
* **階層**、 **Usland**します。
* **インスペクター**で、**レベルの制御**、確認**を有効にするコラボレーション**します。

### <a name="digging-into-the-code"></a>コードをについてください。

ここで見て LevelControl.cs します。 このスクリプトでは、ゲーム ロジックの中核となるはし、ゲームの状態を保持します。 これは UNET を使用して、マルチ プレーヤー ゲームからデータの流れも、少なくともこのチュートリアルを変更するかを理解する必要があります。 UNET のより詳細な概要については、Unity のドキュメントを参照してください。

[プロジェクト] パネルに移動します**Assets\AppPrefabs\Support\Scripts\GameLogic**ダブルクリックして**LevelControl.cs**します。

イマーシブ ヘッドセットが、ロケットの準備ができていることを示す方法を説明しましょう。 ロケット起動の準備は、島に 3 つのパスに対応するブールの一覧で次の 3 つのブールのいずれかを設定して伝達されます。 ロケット ルーム茶色パッド上に、パスに割り当てられたユーザーの場合は、パスのブール値が設定されます。 では、詳細にようになりました。

私たちは、Update() 関数で開始されます。 'チート' 関数があることに注意してください。 使用してこの開発で、ロケットをテストし、シーケンスをリセットしました。 マルチ ユーザーのエクスペリエンスでは機能しません。 できれば次の情報が内在化時間で行うことができます動作します。 かどうか、ローカルのプレーヤーが専念した状態を確認します後ずるをかどうかを確認します。 目標にしていることを探す方法に注目します。 場合は、内部で (専念した状態) を確認する CheckGoal の背後にある非表示の呼び出しは、 **EnableCollaboration** bool。 これは、この章の手順を実行中にオンにしたチェック ボックスをオンに対応します。 内部 EnableCollaboration CheckGoal() への呼び出しがわかります。

CheckGoal は、いくつかの数学、パッドを越えますが多いか少ないかどうかを参照してください。 ときに Debug.Log「目標に着荷済」し、そこで 'SendAtGoalMessage()' を呼び出します。 SendAtGoalMessage で playerController.SendAtGoal と呼んでいます。 いくつかの時間を節約するには、次のコードに示します。

```cs
private void CmdSendAtGoal(int GoalIndex)
       {
           levelState.SetGoalIndex(GoalIndex);
       }
```

```cs
public void SendAtGoal(int GoalIndex)
       {
           if (isLocalPlayer)
           {
               Debug.Log("sending at goal " + GoalIndex);
               CmdSendAtGoal(GoalIndex);
           }
       }
```

SendAtGoalMessage CmdSendAtGoal、どの呼び出し levelState.SetGoalIndex、LevelControl.cs に戻ります。 これを呼び出すことに注意してください。 これは一見奇妙な見えます。 なぜ呼び出せばこれではなく SetGoalIndex player コント ローラーを介してルーティング奇妙なでしょうか。 理由は、私たちが UNET はデータの同期を保つを使用してデータ モデルに一致します。ずるをしてスラッシングを防ぐには、UNET は、各オブジェクトに同期された変数を変更する権限を持つユーザーが含まれている必要があります。 さらに、(セッションを開始したユーザー) のホストだけでは、データを直接変更することができます。 ホストではありませんが、権限を持つユーザーは、変数を変更するホストに 'command' を送信する必要があります。 既定では、ホストは、ユーザーを表す生成されたオブジェクトを除く、すべてのオブジェクトに対して権限を持ちます。 ここでは、このオブジェクトには、playercontroller スクリプトがあります。 オブジェクトの権限を要求し、変更する方法がありますが、player コント ローラーは、player コント ローラーを介して自己の機関とルート コマンドであるという事実を利用してを選択します。

目標で自分たちが見つかった場合は、プレーヤーは、ホストに通知する必要がありますホストには、その他のユーザー通知は、別の方法と言われます。

LevelControl.cs SetGoalIndex 見てに戻る ここで synclist (AtGoal) に値の値を設定します。 このような処理中に、ホストのコンテキストでは注意してください。 コマンドと同様に、RPC は、ホストを発行できますが、いくつかのコードを実行するすべてのクライアントです。 ここで 'RpcCheckAllGoals' を呼び出します。 各クライアントは個別にかどうかは、すべての 3 つ AtGoals が設定されているかを確認してくださいと、そうである場合は、ロケットを起動します。

### <a name="enjoy-your-progress"></a>進行状況をお楽しみください。

前のチャプターに基づき、私たちの前としてセッションが開始されます。 この時間を自分のパスで、「ドア」をイマーシブ ヘッドセット get 内のユーザーとして HoloLens ユーザーのみが認識できることツールヒントが表示されます。 HoloLens のユーザーは、イマーシブ ヘッドセットのユーザーにこの手掛かりの通信を担当します。 火山内の対応する茶色パッドに各アバターがステップ インしたら、ロケットが領域を起動します。 もう一度行うことができますので、60 秒後に、シーンがリセットされます。

## <a name="see-also"></a>関連項目
* [MR 入力 213:アニメーション コント ローラー](mixed-reality-213.md)