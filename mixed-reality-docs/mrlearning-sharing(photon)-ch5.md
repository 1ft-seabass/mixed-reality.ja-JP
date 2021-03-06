---
title: 複数ユーザー機能のチュートリアル-5. Azure 空間アンカーを共有エクスペリエンスに統合する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553810"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Azure 空間アンカーを共有エクスペリエンスに統合する

このレッスンでは、Azure 空間アンカー (ASA) を共有エクスペリエンスに統合する方法について説明します。 ASA を使用すると、複数の併置されたデバイスは、物理環境で仮想エクスペリエンスを固定して、すべての参加者が同じ物理的な場所にオブジェクトを表示するようにすることができます。

## <a name="objectives"></a>目標

* ASA を複数デバイスのアラインメントの共有エクスペリエンスに統合します。
* ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについて説明します。

## <a name="instructions"></a>手順

1. MixedRealityPlayspace 親オブジェクトの下にある TableAnchor prefab を選択し、削除します。

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. [プロジェクト] ビューで、[資産-> Resources-> Prefabs] に移動し、SharedPlayground オブジェクトの上に TableAnchor prefab をドラッグして子にします。

3. MixedRealityPlayspace 親オブジェクト TableAnchor オブジェクトを展開し、[ボタン] オブジェクトも展開します。

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. ここで、階層内で [ShareAzureAnchorButton] を選択し、注意をインスペクターパネルに移動します。 下の画像に表示されているドロップダウンメニューまで下にスクロールし、[AnchorModuleScript] を選択して、[ShareAnchorNetwork ()] をクリックします。

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. [GetAzureAnchorButton] (手順4を参照) を選択して、注意をインスペクターパネルに移動します。 下の画像に表示されているドロップダウンメニューまで下にスクロールし、[AnchorModuleScript] を選択し、[GetSharedAnchorNetwork ()] をクリックして、[保存] をクリックします。

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. 手順4を繰り返して、StartAzureSession () 関数を StartAzureSessionButton にフックします。

7. 手順 4. を繰り返して、CreateAzureAnchor () 関数を CreateAzureAnchorButton にフックし、TableAnchor オブジェクトが関数のパラメーター "Game Object" フィールドに割り当てられていることを確認します。

8. 「[シーンを azure リソースに接続](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)する」の指示に従って、Azure 空間アンカーサービスの資格情報を追加します。

9. 共有モジュールをテストするには、[Azure ASA セッションの開始] ボタンをクリックして azure 空間アンカーセッションを開始し、[Azure アンカーの作成] ボタンをクリックして azure アンカーを作成します。 Azure アンカーが作成されるまで待ちます。 Azure アンカーが作成されたら、[Azure アンカーを共有する] ボタンをクリックして、作成した azure アンカーを HoloLens から共有します。

10. 別の HoloLens で共有 azure アンカーを受信するには、[Azure ASA セッションを開始します] をクリックして開始し、現在の ASA セッションにアクセスします。

11. [Get Azure Anchor] \ (Azure アンカーの取得 \) ボタンをクリックして、他の HoloLens から共有 azure アンカーを取得します。

## <a name="congratulations"></a>結論

このレッスンでは、Azure の強力な新しい空間アンカーを統合して、共有された環境に併置されたデバイスを配置する方法について学習しました。 これにより、共有モジュールも終了します。 新しい Photon アカウントを設定し、Photon とさしあたっを新しい Unity アプリケーションに統合し、アバターと共有オブジェクトを構成し、最後に ASA を使用して複数の参加者を配置する方法を学習しました。
