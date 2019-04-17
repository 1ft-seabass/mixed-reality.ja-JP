---
title: 音声のデザイン
description: 視線、ジェスチャ、音声 (GGV) は、HoloLens の相互作用の主要な手段です。 この記事では、音声の設計に思慮深いガイダンスを提供します。
author: rwinj
ms.author: randyw
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、対話、音声
ms.openlocfilehash: 2df0e15c66891b08577fcf203d11f7c7008247f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604141"
---
# <a name="voice-design"></a>音声のデザイン

視線、ジェスチャ、音声 (GGV) は、HoloLens の相互作用の主要な手段です。 [視線](gaze.md)と併用、[カーソル](cursors.md)はユーザーと対話する準備ができるコンテンツの対象にするためのメカニズムです。 [ジェスチャ](gestures.md)または[音声](voice-input.md)は意図機構です。 視線の先は、相互作用を完了するジェスチャまたは音声のいずれかで使用できます。

イマーシブ ヘッドセット、相互作用の主要な手段には視線の先にコミットとポイント-コミット (で、[モーションのコント ローラー](motion-controllers.md))。 ユーザーの音声機能を備えたヘッドセットの場合は、操作が完了する視線の先またはポイントとの組み合わせで音声が使用できます。

アプリを設計するときに、これらのインタラクションがうまく機能を利用する方法を検討してください。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> 音声</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (とヘッドセットがアタッチされている)</td>
</tr>
</table>



## <a name="how-to-use-voice"></a>音声を使用する方法

ビルドする経験に音声コマンドを追加することを検討してください。 音声は、強力かつ便利な方法は、システムとアプリを制御します。 ユーザーは、さまざまな言語とアクセントと話し、いるために、音声キーワードの適切な選択肢がユーザーのコマンドが明確に解釈されることを確認することができます。

### <a name="best-practices"></a>ベスト プラクティス

滑らかな音声認識に役立ついくつかのプラクティスを以下に示します。
* **簡潔なコマンドを使用して**- 可能であれば、2 つ以上の音節文字のキーワードを選択します。 1 音節単語は、別のアクセントの担当者が読み上げるときに、別の母音サウンドを使用する傾向があります。 以下に例を示します。「現在選択されているビデオを再生」より優れた「ビデオを再生」が
* **単純なボキャブラリを使用して、** -例。「Show プラカード」よりも優れていますが「表示に注意してください」
* **コマンドが非破壊的な確認**- 音声認識コマンドを実行できるすべての操作は非破壊的なことを確認し、簡単にできる場合は、ユーザーの近くの読み上げを誤って別のユーザーがコマンドを開始します。
* **ような発音コマンドを避ける**-非常に類似した複数の音声コマンドを登録しないようにします。 以下に例を示します。「詳細を表示する」と"store が表示"には、ほぼ発音を指定できます。
* **使用していない場合、アプリの登録を解除**- アプリが特定の音声コマンドが、有効な状態にないその他のコマンドは、1 つの混乱しないように登録を解除を検討してください。
* **別のアクセント付きテスト**-別のアクセントのユーザーとアプリをテストします。
* **音声コマンドの一貫性を維持**- 前のページには「戻る」の場合、アプリケーションでは、この動作を維持します。
* **システムのコマンドを使用しないように**-次の音声コマンドは、システムの予約されています。 これらは、アプリケーションでない使用する必要があります。
   * "こんにちは Cortana"
   * "Select"

### <a name="what-users-can-say"></a>ユーザーが言うことができます。

ユーザーは、視線の先、またはポイントのいずれかのボタンをターゲットとは、単語を言います **"Select"** そのボタンをアクティブ化します。 "Select"は、常にリッスンする低電力キーワードのいずれかです。 進んで、ユーザーも使用できます"ボタン文法"、システム全体またはアプリ。 たとえば、アプリを見ているときにユーザーと言えます"Remove"(これは、アプリ バーでは) のコマンドは、世界中からアプリを削除します。

### <a name="see-it-say-it"></a>表示、」ということ

Windows Mixed Reality で「認識, に言って」音声モデルが採用されている場所**ボタンにラベルが関連付けられている音声コマンドと同一**します。 ラベルと音声コマンドの間の任意の dissonance 存在しないため、ユーザーを理解できる何を言おうシステムを制御します。 このボタンをもたらす中に補強するために、 **「音声は、ヒントを下げなければ」** ボタンが有効になっている音声通信が表示されます。

![例 1」ということを確認します。](images/voice-seeitsayit1-640px.jpg)

![例 2 と答えるを参照してください。](images/voice-seeitsayit2-640px.jpg)<br>
*例については「を参照してください、たとえば、」*

### <a name="voices-strengths"></a>音声の長所

音声入力は、当社のインテントを通信するために自然な方法です。 音声がインターフェイスに特に適して**トラバーサル**(ユーザーがあります「と言います戻る」を検索中に Web ページのセットアップし、アプリに戻る ボタンをクリックすることではなく) インターフェイスの複数の手順をユーザーがカットのに役立つためです。 この小さな時間の節約は、強力な**感情的な効果**でユーザーのエクスペリエンスの認識と少量の後押しを提供します。 音声を使用しても便利な入力方法または完全な腕をしましたが、ときに**マルチタスク**します。 キーボードで入力することは困難であり、デバイスで**ディクテーションを音声**効率的な方法を入力することができます。 最後に、場合によってはときに、**精度の範囲**視線、ジェスチャは、制限は、音声がありますユーザーの入力メソッドを信頼できるのみです。

**音声を使用してがどのようにメリット ユーザー**
* 時間の短縮、最終目的をより効率的に行う必要があります。
* -労力を最小限に抑えられますよりスムーズになり、簡単なタスクください。
* Cognitive 負荷の軽減が直感的で簡単に学び、注意してください。
* これはしれませんで、動作の観点から社会に関する規範を適合する必要があります。
* これのルーチンの音声が常習的な動作になることができます簡単にします。

### <a name="voices-weaknesses"></a>音声の短所

音声では、いくつか短所もあります。 詳細に制御は、その 1 つです。 (たとえば、ユーザー「発生」と言うことがどの程度と答えることはできません。 「少し」を定量化する困難です。 移動または音声でモ ノのスケーリングは困難です (音声はコントロールの粒度を提供していません)。 音声が完璧なこともできます。 場合ボイス システムは正しくコマンドを聞くことや、お待ちしておりますコマンドが失敗しました。 このようなエラーからの回復は、任意のインターフェイスに課題です。 最後に、音声はソーシャル許容できない公共の場所にします。 ユーザーがならまたはできないいくつかの点があります。 これらの崖が最も得意使用する音声認識を許可します。

### <a name="voice-feedback-states"></a>音声のフィードバックの状態

音声が正しく適用されると、ユーザーが理解**何ができるし、答えて、フィードバックを取得**システム**正しくを聞いた**します。 これら 2 つのシグナルは、プライマリの入力として音声を使用して確信を持てるユーザーを確認します。 何を示す図が音声入力が認識されると、カーソルとユーザーに通信する方法を次に示します。

![カーソルの音声フィードバック状態](images/voicefeedbackstates.png)<br>
*カーソルの音声フィードバック状態*

## <a name="top-things-users-should-know-about-speech-on-windows-mixed-reality"></a>最上位のモ ノのユーザーは、"speech"Windows Mixed Reality on について 必要があります。
* たとえば **"Select"** (anywhere を使用このボタンをクリックする) ボタンを対象とします。
* 指定すると、**アプリ バー ボタンのラベル名**処置を実行する一部のアプリでします。 たとえば、アプリを見ているときに、ユーザーことができますコマンドを言う"Remove"、世界中からアプリを削除する (この時間を節約、手でそれをクリックする必要がなくなります)。
* Cortana のことを示すリッスンを開始する**コルタナさん」。** 自分の質問 (」「コルタナさん高さは Eiffel tower)、(」「コルタナさん Netflix がオープン)、アプリを開くするように指示するまたは ("「コルタナさん、ホームを) [スタート] メニューを表示するように指示するとします。

## <a name="common-questions-and-concerns-users-have-about-voice"></a>音声に関する質問や問題の一般的なユーザーがあります。
* 何も言えません。
* システムが正しく me 聞こえるかを確認する方法
   * システムに続けて、音声コマンドが正しくないいます。
   * 音声コマンドを指定すると、反応がないです。
* 音声コマンドを指定すると、間違ったやり方を反応します。
* 自分の音声を特定のアプリまたはアプリのコマンドを対象する方法を教えてください。
* HoloLens で音声コマンドいろいろ holographic のフレームを使用できますか。

## <a name="see-also"></a>関連項目
* [ジェスチャ](gestures.md)
* [視線の先を対象とします。](gaze-targeting.md)