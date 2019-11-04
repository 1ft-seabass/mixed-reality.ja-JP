---
title: Unity を使用したマネージデバッグ IL2CPP
description: この記事では、Unity IL2CPP UWP プロジェクトでマネージデバッガーを実行する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity、visual studio、デバッグ、il2cpp
ms.openlocfilehash: fd09c3ca1bd410c56e46eb8e8815742f87482d08
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439633"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="f9c1b-104">Unity を使用したマネージデバッグ IL2CPP</span><span class="sxs-lookup"><span data-stu-id="f9c1b-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="f9c1b-105">マネージデバッガーを Unity IL2CPP UWP ビルドにアタッチするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="f9c1b-106">このガイドは、初めて HoloLens および HoloLens 2 用に開発されました。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="f9c1b-107">[マルチキャスト](https://en.wikipedia.org/wiki/Multicast)をサポートしているネットワーク上に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="f9c1b-108">UWP 発行設定機能の下で、 **Internet Clientserver**と**PrivateNetworkClientServer**が Unity でチェックインされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![UWP 発行設定機能](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="f9c1b-110">Unity UWP ビルド設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="f9c1b-111">開発ビルド</span><span class="sxs-lookup"><span data-stu-id="f9c1b-111">Development Build</span></span>
    - <span data-ttu-id="f9c1b-112">スクリプト デバッグ</span><span class="sxs-lookup"><span data-stu-id="f9c1b-112">Script Debugging</span></span>
    - <span data-ttu-id="f9c1b-113">マネージデバッガーを待機する (省略可能)</span><span class="sxs-lookup"><span data-stu-id="f9c1b-113">Wait for Managed Debugger (optional)</span></span>

    ![UWP ビルドの設定](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="f9c1b-115">Unity でビルドします。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-115">Build in Unity.</span></span>
1. <span data-ttu-id="f9c1b-116">Visual Studio ソリューションからデバイスにビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="f9c1b-117">**デバッグ**構成または**リリース**構成を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="f9c1b-118">**マスター**構成によって Unity プロファイラーが無効になり、最適なデバッグができなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="f9c1b-119">必要に応じて、ソリューションの package.appxmanifest の [機能] ボックスの一覧で、**インターネット (クライアント & サーバー)** と**プライベートネットワーク (クライアント & サーバー)** を確認します。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="f9c1b-120">デバイスでアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-120">Start the app on your device.</span></span> <span data-ttu-id="f9c1b-121">デバイスが PC と同じネットワークに接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="f9c1b-122">デバイスが USB 経由で PC に接続されて**いない**ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="f9c1b-123">Unity のスクリプトをダブルクリックすると作成される Visual Studio ソリューションに移動します。ここでスクリプトを表示およびC#編集できます。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-123">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="f9c1b-124">デバッグ-> Unity デバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-124">Debug -> Attach Unity Debugger.</span></span>

    ![Unity デバッガーのアタッチ](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="f9c1b-126">一覧からデバイスを選択し、[OK] をクリックして接続します。</span><span class="sxs-lookup"><span data-stu-id="f9c1b-126">Select your device in the list and click "OK" to attach.</span></span>

    ![デバイス一覧](images/il2cpp-debugging-machines.png)