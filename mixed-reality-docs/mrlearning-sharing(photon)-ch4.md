---
title: 複数ユーザー機能のチュートリアル-4. オブジェクトの移動を複数のユーザーと共有する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: 56f7c767323285453cbeea9034f97a7c14e92359
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885626"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. オブジェクトの移動を複数のユーザーと共有する

このチュートリアルでは、共有セッションのすべての参加要素が相互に共同作業したり、他のユーザーの操作を表示したりできるように、オブジェクトの移動を共有する方法を学習します。 このレッスンは、[基本モジュールチュートリアル](mrlearning-base.md)の一部として作成された太陰暦ランチャーに基づいています。

## <a name="objectives"></a>目標

- 共有する3D モデルとして旧暦ランチャーを使用する
- 3D モデルの移動を共有するようにプロジェクトを構成する
- 基本的なマルチユーザーコラボレーションアプリケーションを構築する方法について説明します

## <a name="instructions"></a>手順

1. 前のレッスン (コントロール + S) からシーンを保存します。 必要なときに簡単に見つけられるように、HLSharedProjectMainPart4 という名前を指定できます。

2. [プロジェクト] ウィンドウの [Assets-> Scripts] フォルダーで、[GenericNetSync] をダブルクリックして、Visual Studio または使用しているコードエディターで開きます。  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. 34および38行では、"//" を削除して、このレッスンで使用するテーブルのコードをアクティブ化します。 次に、ファイルを保存します。

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. [プロジェクト] ウィンドウで、[Assets-> Scripts] フォルダー内の PhotonRoom.cs ファイルをダブルクリックして、Visual Studio で開きます。

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. 手順 3. と同じように、"//" を削除してコードをアクティブにする必要があります (25、26、106行)。

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. [階層] ビューで、NetworkRoom オブジェクトを選択します。

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. プロジェクト ビューで、資産-> Resources-> Prefabs に移動します。 まず、テーブル prefab を PhotonRoom クラスの Tableprefab スロットにドラッグアンドドロップします。 次に、RocketLauncherCompleteVariantprefab を PhotonRoom クラスのモジュール Prefab スロットにドラッグアンドドロップします。

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >Prefab オブジェクトとリリースのいずれかをクリックすると、インスペクターがそのオブジェクトに切り替わります。 各オブジェクトをクリックし、ドラッグしてドロップし、各オブジェクトを適切なスロットに解放します。

8. MixedRealityPlayspace の左側にある矢印をクリックし、子ゲームオブジェクト MainCamera を SharedPlayground グラウンドに移動します。 次に、prefab を削除し、キーボードの [削除] をタップして、MixedRealityPlayspace を削除します。

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >メインカメラと SharedPlayground グラウンドの両方の位置が0、0、0に設定されていることを確認します。

9. "SharedPlayground グラウンド" オブジェクトを選択し、マウスを右クリックして [空の作成] オプションを選択し、空のゲームオブジェクトを "SharedPlayground グラウンド" ゲームオブジェクトの子として作成します。

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. 階層で新しいオブジェクトを選択し、[インスペクター] パネルでオブジェクトの名前を TableAnchor に変更します。 また、[コンポーネントの追加] をクリックし、TableAnchor コンポーネントを検索します。 それを選択してオブジェクトに追加します。

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. Prefabs フォルダーの [プロジェクト] パネルで、テーブル prefab を、先ほど作成した "TableAnchor" 子オブジェクトにドラッグします。

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)
   
12. 資産-> Resources-> Prefabs から、"ロケット Launcher_Complete バリアント" prefab を開きます。

13. "LunarModule" を選択し、"Photon Transform View" と "Photon View" という2つのコンポーネントを追加します。

14. "LunarModule" の "検出" オブジェクトが選択された状態で、"Photon Transform View" コンポーネントを "Photon View" コンポーネントの "観察されたコンポーネント" スロットにドラッグします。

## <a name="congratulations"></a>結論

この処理が完了したら、次のようにして、旧暦モジュールを見つけます。 その後、Unity プロジェクトに参加するすべてのユーザーが、旧暦ランチャーを移動できます。  すべての移動が同期されるため、各ユーザーが互いの相互作用を参照できます。 これらの概念は、すべての機能を備えた共有コラボレーションエクスペリエンスの基本的な構成要素として機能します。

すべてのユーザーは共有エクスペリエンスの一部として接続されており、オブジェクトの相対的な移動を確認できますが、アプリケーションでは、ローカルユーザーが他のオブジェクトとオブジェクトを表示できないように、アバターとオブジェクトを正確に配置することはできません。物理的な世界。 ローカルの共有エクスペリエンスを固定するために、すべてのデバイスは物理環境についてよく理解している必要があります。 このモジュールでは、次のレッスンで実装する[Azure 空間アンカー](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) を使用してこれを実現します。

次のレッスンに進む前に、asa の基本、Azure アカウントとリソースの作成、およびその他の基本的なビルディングブロックについて説明する ASA Learning モジュールを完成させる必要があります。これは、共有エクスペリエンスに統合する前に必要です。

[次のレッスン: 5. Azure 空間アンカーを共有エクスペリエンスに統合する](mrlearning-sharing(photon)-ch5.md)
