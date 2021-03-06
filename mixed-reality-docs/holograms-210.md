---
title: MR 入力 210-宝石
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、宝石の概念の詳細を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、宝石
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434685"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルは、HoloLens (第1世代) と Mixed Reality イマーシブヘッドセットを念頭に置いて設計されています。  そのため、これらのデバイスの開発に関するガイダンスをまだ探している開発者には、これらのチュートリアルを残しておくことが重要です。  これらのチュートリアルは、HoloLens 2 に使用されている最新のツールセットまたは相互作用では更新され **_ません_** 。  サポートされているデバイスでの作業を続行するために管理されます。 HoloLens 2 については[、新しい一連のチュートリアル](mrlearning-base.md)が投稿されています。

# <a name="mr-input-210-gaze"></a>MR 入力 210: 宝石

[見つめ](gaze-and-commit.md)は入力の最初の形式であり、ユーザーの意図と認識を明らかにします。 MR 入力 210 (プロジェクトエクスプローラーとも呼ばれます) は、Windows Mixed Reality 向けの、宝石に関連する概念について詳しく説明しています。 私たちは、カーソルとホログラムにコンテキスト認識を追加し、アプリがユーザーの宝石について認識していることを最大限に活用します。

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

ここでは、宝石の概念を理解するのに役立つわかりやすい astronaut を用意しています。 [MR 基本 101](holograms-101.md)では、簡単なカーソルを使用して、宝石を見つめます。 現在、単純なカーソルを超えてステップを移動しています。

* カーソルとホログラムを見つめています。どちらも、ユーザーが探している場所またはユーザーが探し*ていない*場所に基づいて変化します。 これにより、コンテキスト対応になります。
* カーソルとホログラムにフィードバックを追加して、対象となっている内容についてユーザーにより多くのコンテキストを提供します。 このフィードバックは、オーディオとビジュアルにすることができます。
* ここでは、ユーザーがより小さなターゲットをヒットするのを支援するための手法について説明します。
* 方向性のあるインジケーターを使用して、ユーザーの注意をホログラムに描画する方法について説明します。
* ここでは、ユーザーが世界中に移動するときに、ホログラムを使用する手法について説明します。

>[!IMPORTANT]
>以下の各章に埋め込まれているビデオは、古いバージョンの Unity と Mixed Reality Toolkit を使用して記録されています。 ステップバイステップの手順は正確であり、最新のものですが、最新ではない対応するビデオにスクリプトとビジュアルが表示される場合があります。 ビデオはために含まれています。ここで説明する概念は引き続き適用されます。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>まで</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 入力 210: 宝石</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* 適切な[ツールがインストール](install-the-tools.md)された WINDOWS 10 PC。
* 基本的なC#プログラミング機能。
* [MR の基本 101](holograms-101.md)を完了している必要があります。
* [開発用に構成され](using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。

### <a name="project-files"></a>プロジェクトファイル

* プロジェクトに必要な[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)をダウンロードします。 Unity 2017.2 以降が必要です。
* ファイルをデスクトップまたはその他の簡単な場所に保管します。

>[!NOTE]
>ダウンロードする前にソースコードを確認する場合は、GitHub から[入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)ます。

### <a name="errata-and-notes"></a>エラッタとメモ

* Visual Studio で、コード内のブレークポイントにヒットするには、[ツール]-[> オプション] >-[デバッグ] の下にある [マイコードのみ] を無効 (オフ) にする必要があります。

## <a name="chapter-1---unity-setup"></a>章 1-Unity のセットアップ

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>目標

* HoloLens 用 Unity の開発を最適化する。
* アセットをインポートし、シーンをセットアップする。
* HoloLens で astronaut を表示します。

### <a name="instructions"></a>手順

1. Unity を起動します。
2. **[新しいプロジェクト]** を選択します。
3. プロジェクトに**Modelexplorer**という名前を指定します。
4. 以前にアーカイブしていない、場所を**見つめ**フォルダーとして入力します。
5. プロジェクトが **[3D]** に設定されていることを確認します。
6. **[プロジェクトの作成]** をクリックします。

### <a name="unity-settings-for-hololens"></a>HoloLens の Unity 設定

エクスポートしようとしているアプリが2D ビューではなく[イマーシブビュー](app-views.md)を作成する必要があることを Unity に知らせる必要があります。 これを行うには、HoloLens を仮想現実デバイスとして追加します。

1. **[Edit > Project Settings > Player]** にアクセスします。
2. [プレーヤー設定] の [**インスペクター] パネル**で、 **[Windows ストア]** アイコンを選択します。
3. **[XR Settings]** グループを展開します。
4. **[表示]** セクションで、 **[サポートされている仮想現実]** チェックボックスをオンにして、新しい**仮想現実の sdk**リストを追加します。
5. **[Windows Mixed Reality]** が一覧に表示されていることを確認します。 表示されていない場合は、一覧の下部にある [ **+** ] ボタンを選択し、 **[Windows Holographic]** を選択します。

次に、スクリプトバックエンドを .NET に設定する必要があります。

1. **Edit > Project Settings > Player** (これは前の手順のままである場合があります) に進みます。
2. [プレーヤー設定] の [**インスペクター] パネル**で、 **[Windows ストア]** アイコンを選択します。
3. **[その他の設定]** 構成セクションで、 **[スクリプトバックエンド]** が **[.net]** に設定されていることを確認します。

最後に、HoloLens で高速なパフォーマンスを実現するために品質設定を更新します。

1. 編集]  **[> プロジェクトの設定]** [品質 > にアクセスします。
2. Windows ストアアイコンの下の**既定**の行で、下向き矢印をクリックします。
3. **Windows ストアアプリ**の場合は **[低]** を選択します。

### <a name="import-project-assets"></a>プロジェクト資産のインポート

1. **[プロジェクト]** パネルの **[アセット]** フォルダーを右クリックします。
2. **[パッケージのインポート > カスタムパッケージ]** をクリックします。
3. ダウンロードしたプロジェクトファイルに移動し、 **Modelexplorer. unitypackage**をクリックします。
4. **[開く]** をクリックします。
5. パッケージが読み込まれたら、 **[インポート]** ボタンをクリックします。

### <a name="setup-the-scene"></a>シーンを設定する

1. 階層で、**メインカメラ**を削除します。
2. **HoloToolkit**フォルダーで、 **Input**フォルダーを開き、 **Prefabs**フォルダーを開きます。
3. **MixedRealityCameraParent** Prefab を**Prefabs**フォルダーから**階層**にドラッグアンドドロップします。
4. 階層内の**指向性ライト**を右クリックし、 **[削除]** を選択します。
5. **[ホログラム]** フォルダーで、次のアセットを**階層**のルートにドラッグアンドドロップします。
    * **AstroMan**
    * **ライト**
    * **Space Audiosource**
    * **スペースの背景**
6. Astronaut を表示するには、**再生モード**を開始▶します。
7. **再生モード**▶もう一度クリックして**停止**します。
8. **ホログラム**フォルダーで、[ **fitbox]** 資産を見つけて、**階層**のルートにドラッグします。
9. **階層** パネルで  **Fitbox チェックボックス**をオンにします。
10. **AstroMan**コレクションを**階層**から、 **[インスペクター]** パネルの Fitbox ボックスの **[ホログラムコレクション]** プロパティにドラッグします。

### <a name="save-the-project"></a>プロジェクトを保存する

1. 新しいシーンを保存します。 **ファイル > シーンを名前を付けて保存**します。
2. **[新しいフォルダー]** をクリックし、フォルダーに「**シーン**」という名前を指定します。
3. ファイルに "**Modelexplorer**" という名前を付け、 **[シーン]** フォルダーに保存します。

### <a name="build-the-project"></a>プロジェクトをビルドする

1. Unity で、 **[ファイル > ビルド設定]** を選択します。
2. シーンを追加するには、[開いている**シーンの追加**] をクリックします。
3. **[プラットフォーム]** ボックスの一覧の **[ユニバーサル Windows プラットフォーム]** を選択し、 **[プラットフォームの切り替え]** をクリックします。
4. HoloLens 向けに特に開発している場合は、**ターゲットデバイス**を**hololens**に設定します。 それ以外の場合は、**任意のデバイス**に残しておきます。
5. **ビルドの種類**が **[D3D]** に設定され、 **[sdk]** が **[最新のインストール済み]** に設定されていることを確認します (sdk 16299 以降である必要があります)。
6. **[Build]** をクリックします。
7. "App" という名前の**新しいフォルダー**を作成します。
8. **アプリ**フォルダーをシングルクリックします。
9. **[フォルダーの選択]** をクリックします。

Unity が完了すると、エクスプローラーウィンドウが表示されます。

1. **アプリ**フォルダーを開きます。
2. **Modelexplorer Visual Studio ソリューション**を開きます。

HoloLens に展開する場合:

1. Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に変更し、ARM から**x86**に変更します。
2. ローカルコンピューター ボタンの横にあるドロップダウン矢印をクリックし、**リモートコンピューター** を選択します。
3. **HoloLens デバイスの IP アドレス**を入力し、[認証モード] を [**ユニバーサル (暗号化**されていないプロトコル)] に設定します。 [**選択] を**クリックします。 デバイスの IP アドレスがわからない場合は、**設定 Network & Internet > 詳細オプション >** 確認してください。
4. 上部のメニューバーで、デバッグ、**デバッグなしで開始** の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。 初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](using-visual-studio.md#pairing-your-device)する必要があります。
5. アプリが展開されたら、 **select ジェスチャ**を使用して、 **[fitbox]** を閉じます。

イマーシブヘッドセットに展開する場合:

1. Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから**リリース**に、ARM から**x64**に変更します。
2. 配置ターゲットが**ローカルコンピューター**に設定されていることを確認します。
3. 上部のメニューバーで、デバッグ、**デバッグなしで開始** の順にクリック >、Ctrl キーを押し**ながら F5**キーを押します。
4. アプリがデプロイされたら、モーションコントローラーでトリガーをプルして、 **Fitbox ボックス**を閉じます。

## <a name="chapter-2---cursor-and-target-feedback"></a>第2章-カーソルとターゲットのフィードバック

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>目標

* カーソルの視覚的なデザインと動作。
* 見つめ based のカーソルフィードバック。
* 宝石によるホログラムフィードバック。

ここでは、いくつかのカーソルデザインの原則に基づいて作業を行います。

* カーソルは常に存在します。
* カーソルが小さすぎるか、または大きくならないようにしてください。
* Obstructing コンテンツは避けてください。

### <a name="instructions"></a>手順

1. **HoloToolkit\Input\Prefabs**フォルダーで、 **inputmanager**資産を見つけます。
2. **Inputmanager**を**階層**にドラッグアンドドロップします。
3. **HoloToolkit\Input\Prefabs**フォルダーで、**カーソル**アセットを見つけます。
4. **カーソル**を**階層**にドラッグアンドドロップします。
5. **階層**内の**inputmanager**オブジェクトを選択します。
6. **インスペクター**の下部にあるカーソルオブジェクトを、**階層**から Inputmanager の**Simplesingleポインタセレクター**の**cursor**フィールドに**ドラッグします**。

![単純な単一ポインターセレクターの設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>ビルドと配置

1. **ファイル > ビルド設定**からアプリをリビルドします。
2. **アプリフォルダー**を開きます。
3. **Modelexplorer Visual Studio ソリューション**を開きます。
4. [**デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し**ながら F5**キーを押します。
5. カーソルの描画方法と、ホログラムに触れている場合の外観の変化を確認します。

### <a name="instructions"></a>手順

1. **[階層]** パネルで、[ **AstroMan**->**GEO_G**->**Back_Center** ] オブジェクトを展開します。
2. **Interactible.cs**をダブルクリックして、Visual Studio で開きます。
3. **Interactible.cs**の**OnFocusEnter ()** および**OnFocusExit ()** コールバックの行をコメント解除します。 これらは、(宝石またはコントローラーをポイントすることによって) フォーカスが特定のオブジェクトの collider を出入りするときに、Mixed Reality Toolkit の InputManager によって呼び出されます。

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>上記の `EnableKeyword` と `DisableKeyword` を使用します。 ツールキットの標準シェーダーを使用して独自のアプリでこれらを使用するには、スクリプトを使用して[マテリアルにアクセスするための Unity ガイドライン](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)に従う必要があります。 この例では、リソースフォルダーに必要な、強調表示された[3 つの素材](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)が既に含まれています (名前に強調表示された3つの素材を探します)。

### <a name="build-and-deploy"></a>ビルドと配置

1. 前と同様に、プロジェクトをビルドし、HoloLens にデプロイします。
2. 1つのオブジェクトを対象としていて、そうでない場合はどうなるかを観察します。

## <a name="chapter-3---targeting-techniques"></a>章 3-ターゲット手法

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>目標

* ホログラムを簡単にターゲット設定できるようにします。
* 自然な移動を安定化します。

### <a name="instructions"></a>手順

1. **[階層]** パネルで、 **inputmanager**オブジェクトを選択します。
2. **[インスペクター]** パネルで、**宝石**のスクリプトを見つけます。 表示する場合は、これをクリックして Visual Studio で開きます。
    * このスクリプトは、Raycast データのサンプルに対して反復処理を行い、精度のターゲット設定のためにユーザーの宝石を安定化するのに役立ちます。
3. **インスペクター**では、 **[保存された安定性のサンプル]** の値を編集できます。 この値は、安定板が、安定値を計算するために反復処理するサンプルの数を表します。

## <a name="chapter-4---directional-indicator"></a>Chapter 4 方向インジケーター

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>目標

* ホログラムの検索に役立つように、カーソルに方向インジケーターを追加します。

### <a name="instructions"></a>手順

**DirectionIndicator.cs**ファイルを次のように使用します。

1. ユーザーがホログラムを見ていない場合は、方向インジケーターを表示します。
2. ユーザーがホログラムでの表示を切り替えている場合は、方向インジケーターを非表示にします。
3. ホログラムをポイントするように方向インジケーターを更新します。

それでは始めましょう。

1. **階層**パネルで**AstroMan**オブジェクトをクリックし、**矢印をクリック**して展開します。
2. **[階層]** パネルで、[ **AstroMan** **] の [** 方向] を選択します。
3. **[インスペクター]** パネルで、 **[コンポーネントの追加]** ボタンをクリックします。
4. メニューで、検索ボックスの**方向インジケーター**を入力します。 検索結果を選択します。
5. **[階層]** パネルで、 **Cursor**オブジェクトを**インスペクター**の**cursor**プロパティにドラッグアンドドロップします。
6. **[プロジェクト]** パネルの **[ホログラム]** フォルダーで、 **Direction Alindicator**資産を**インスペクター**の**指向性インジケーター**プロパティにドラッグアンドドロップします。
7. アプリをビルドしてデプロイします。
8. ディレクショナルインジケーターオブジェクトを使用して astronaut を見つける方法をご覧ください。

## <a name="chapter-5---billboarding"></a>章 5-Billboarding

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>目標

* Billboarding を使用して、ホログラムが常に直面するようにします。

**Billboard.cs**ファイルを使用して、ユーザーに常に接続されていることを示すために、そのオブジェクトの向きを維持します。

1. **[階層]** パネルで、 **AstroMan**オブジェクトを選択します。
2. **[インスペクター]** パネルで、 **[コンポーネントの追加]** ボタンをクリックします。
3. メニューで、[検索] ボックスに「**ビルボード**」と入力します。 検索結果を選択します。
4. **インスペクター**で、**ピボット軸**を**Y**に設定します。
5. お試しください。 以前と同じように、アプリをビルドしてデプロイします。
6. ビルボードオブジェクトがどのように視点を変更するかに関係なく、どのように表示されるかを確認します。
7. ここでは、 **AstroMan**からスクリプトを削除します。

## <a name="chapter-6---tag-along"></a>Chapter 6-タグに沿って

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>目標

* タグを使用して、ホログラムが部屋の周りをたどるようにします。

この問題に対処する際には、次の設計上の制約があります。

* コンテンツは常に一目でわかるはずです。
* コンテンツは使用できません。
* ヘッドロックコンテンツは不快になります。

ここで使用するソリューションでは、"タグに沿った" 方法を使用します。

タグに沿ったオブジェクトは、ユーザーのビューを完全に離れることができません。 タグは、ユーザーの先頭にラバーバンドでアタッチされたオブジェクトであると考えることができます。 ユーザーが移動すると、完全に離れることなく、ビューの端に向かってスライドします。 ユーザーがタグに沿って gazes すると、より完全に表示されます。

**SimpleTagalong.cs**ファイルを次のように使用します。

1. タグに沿ったオブジェクトがカメラの境界内にあるかどうかを確認します。
2. 視錐ビュー内にない場合は、タグを、視錐のビュー内で部分的に配置します。
3. それ以外の場合は、ユーザーからの既定の距離にタグを配置します。

これを行うには、まず、 **Interactible.cs**スクリプトを変更して**TagalongAction**を呼び出す必要があります。

1. コード演習 6. a (コメント解除行 84 ~ 87) を実行して**Interactible.cs**を編集します。

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

**InteractibleAction.cs**スクリプトは、 **Interactible.cs**と組み合わせて、ホログラムをタップしたときにカスタムアクションを実行します。 この例では、タグに対して特に使用します。

* **Scripts**フォルダーで、[ **TagalongAction.cs** asset] をクリックして Visual Studio で開きます。
* コーディングの演習を完了するか、次のように変更します。
  * **階層**の最上位にある検索バーに「 **ChestButton_Center** 」と入力し、結果を選択します。
  * **[インスペクター]** パネルで、 **[コンポーネントの追加]** ボタンをクリックします。
  * メニューの [検索 **] ボックスに**、「」と入力します。 検索結果を選択します。
  * [**ホログラム**フォルダー] で、資産の**タグ**を検索します。
  * **階層**内の**ChestButton_Center**オブジェクトを選択します。 **プロジェクト** パネルの **tagalong**オブジェクトを、プロパティ にある **オブジェクト**  **にドラッグ**アンドドロップします。
  * **インスペクター**の**tagalong アクション**オブジェクトを、 **Interactible**スクリプトの**Interactible action**フィールドにドラッグします。
* **TagalongAction**スクリプトをダブルクリックして、Visual Studio で開きます。

![Interactible のセットアップ](images/holograms210-interactible.png)

次のものを追加する必要があります。

* TagalongAction スクリプトの実行時関数に機能を追加します (InteractibleAction から継承)。
* Billboarding を gazed オブジェクトに追加し、pivot 軸を XY に設定します。
* 次に、単純なタグをオブジェクトに追加します。

**TagalongAction.cs**のソリューションは次のとおりです。

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* お試しください。 アプリをビルドしてデプロイします。
* コンテンツが注視点の中心に沿っているかどうかを監視しますが、継続的にはブロックしないでください。
