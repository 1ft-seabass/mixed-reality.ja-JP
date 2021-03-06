---
title: ケーススタディ-mixed reality での galaxy の作成
description: Microsoft HoloLens を出荷する前に、開発者コミュニティに、新しいデバイスに対して経験豊富な内部チームビルドを表示するアプリの種類を尋ねました。 5000を超えるアイデアが共有されており、24時間の Twitter の投票の後、優勝者は "Galaxy エクスプローラ" という考え方でした。
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy エクスプローラー、HoloLens、Windows Mixed Reality、アイデアの共有、ケーススタディ
ms.openlocfilehash: 696662eb92371708389f8a128dcee6a61acf1816
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436880"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>ケーススタディ-mixed reality での galaxy の作成

Microsoft HoloLens を出荷する前に、開発者コミュニティに、新しいデバイスに対して経験豊富な内部チームビルドを表示するアプリの種類を尋ねました。 5000を超えるアイデアが共有されており、24時間の Twitter に投票した後、優勝者は[Galaxy エクスプローラ](galaxy-explorer.md)という考え方でした。

Andy Zibits、プロジェクトのアートリーダー、およびチームのグラフィックスエンジニアである Karim Luccin は、Galaxy エクスプローラーでの天の川向 galaxy の正確で対話的な表現を作成するための、アートとエンジニアリングの間の共同作業について説明しています。

## <a name="the-tech"></a>技術

[私たちのチーム](galaxy-explorer.md#meet-the-team)は、3つの開発者、3人のアーティスト、プロデューサー、1人のテスト担当者で構成されており、6週間で完全に機能するアプリを構築しました。これにより、天の川のような優れた方法を習得し、その結果を調べることができます。

HoloLens の能力を最大限に活用して、お客様の生きた空間で3D オブジェクトを直接表示することを望んでいました。したがって、ユーザーが近くに拡大して個々の星を見ることができる現実的な外観の galaxy を作成することにしました.

開発の最初の週では、天の川方法の表記についていくつかの目標がありました。これは、高度、動き、および感覚容量を必要としています。これは、galaxy の形の作成に役立つ星です。

数十億の星を持つアニメーションの galaxy の作成に問題があるのは、更新が必要な1つの要素の数が、HoloLens が CPU を使用してアニメーション化するためのフレームごとに大きすぎるということでした。 このソリューションでは、アートとサイエンスが複雑に組み合わされていました。

## <a name="behind-the-scenes"></a>しくみ

個々の星を調べることができるように、最初の手順は、一度にレンダリングできるパーティクルの数を調べることでした。

### <a name="rendering-particles"></a>描画 (パーティクルを)

現在の Cpu は、直列タスクを処理し、同時にいくつかの並列タスクを (コア数に応じて) 処理する場合に適していますが、Gpu は、何千もの操作を並列処理するよりもはるかに効果的です。 ただし、通常は CPU と同じメモリを共有しないので、CPU < > GPU 間でデータを交換すると、すぐにボトルネックになる可能性があります。 このソリューションでは、GPU 上に galaxy を作成し、GPU 上で完全に稼働させる必要がありました。

さまざまなパターンで何千ものポイントパーティクルを使用してストレステストを開始しました。 これにより、HoloLens で galaxy を取得して、動作した機能と失敗したことを確認することができました。

### <a name="creating-the-position-of-the-stars"></a>星の位置の作成

チームメンバーの1人が、最初のC#位置に星を生成するコードを既に作成しています。 星は楕円上にあり、その位置は (**curveoffset**、 **ellipseSize**、**標高**) で記述できます。 **curveoffset**は楕円に沿った星の角度で、 **ellipseSize**は楕円の次元です。X と Z に沿って、galaxy 内の星の適切な昇格が昇格します。 このため、各スター属性で初期化されるバッファー ([Unity の ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) を作成し、それを GPU に送信して、残りのエクスペリエンスに使用することができます。 このバッファーを描画するには、 [Unity の DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html)を使用します。これにより、galaxy を表す実際のメッシュがなくても、任意のポイントのセットに対してシェーダー (GPU 上のコード) を実行できます。

**CPU**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

私たちは、何千ものパーティクルを含む生の円形パターンから始めました。 これにより、多数のパーティクルを管理し、パフォーマンスの高い速度で実行できるようにする必要があることが証明されましたが、galaxy の全体的な構造には満足できませんでした。 図形を改良するために、回転を使用してさまざまなパターンとパーティクルシステムを試しました。 これらは、パーティクルとパフォーマンスの数が一貫していても、中心の近くにある形状が、現実的ではないとを発していたため、当初は実現されていました。 時間を操作できるようにするための出力が必要でした。また、パーティクルは現実的に動き、galaxy の中心に近いループが発生します。

![このように、回転したさまざまなパターンとパーティクルシステムを試しました。](images/galaxy-patterns-500px.png)

このように、回転したさまざまなパターンとパーティクルシステムを試しました。

私たちのチームは、galaxies の機能についていくつかの調査を行ってきました。これは、"[密度の波理論](https://en.wikipedia.org/wiki/Density_wave_theory)" に基づいて楕円に対してパーティクルを移動できるようにするためのカスタムパーティクルシステムを作成しました。これにより、galaxy のアームは次の領域になります。密度は高くなりますが、トラフィックが詰まっているように一定の流束になります。 これは安定した安定したように見えますが、各星はそれぞれの楕円に沿って移動されるため、実際には腕に沿って移動します。 システムでは、パーティクルが CPU 上に存在することはありません。カードを生成し、GPU 上にすべてを回転させるので、システム全体が単に初期状態 + 時間になります。 次のように進行します。

![GPU レンダリングを使用したパーティクルシステムの進行状況](images/spiral-galaxy-arms-500px.jpg)

GPU レンダリングを使用したパーティクルシステムの進行状況


いくつかの省略記号が追加され、回転するように設定されると、galaxies は、星の動きが収束する "腕" の形成を開始しました。 各楕円パスに沿った星の間隔はランダムに指定されており、各星はランダムに追加されています。 これにより、スター移動と arm 図形のより自然な外観の分布が作成されました。 最後に、中央からの距離に基づいて色を設定する機能を追加しました。

### <a name="creating-the-motion-of-the-stars"></a>星の動きの作成

一般的な星の動きをアニメーション化するには、各フレームに対して一定の角度を追加し、楕円を一定の放射状速度で移動させる必要があります。 これは**Curveoffset**を使用する主な理由です。 これは技術的には適切ではありません。星が楕円の長い方に沿って速く移動しますが、一般的な動きは良いと感じます。

![星が長すぎるほど、エッジで速度が遅くなります。](images/ellipse-movement.jpg)

星が長すぎるほど、エッジで速度が遅くなります。


これにより、各星は (**Curveoffset**、 **ellipseSize**、**標高**、 **age**) によって完全に記述されます。 **age**は、シーンが読み込まれてから経過した合計時間を累積したものです。




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

これにより、アプリケーションの開始時に数十の星が生成され、確立された曲線に沿って単一の星のセットがアニメーション化されました。 すべてが GPU 上にあるため、システムはすべての星を並行して CPU に対して無料でアニメーション化できます。

![白の四角形を描画すると、次のようになります。](images/drawing-white-quads-300px.jpg)

白の四角形を描画すると、次のようになります。



各 quad をカメラにするために、ジオメトリシェーダーを使用して、星のテクスチャを含む画面上の2D 四角形にそれぞれの星の位置を変換します。

![四角形ではなくダイヤ。](images/drawing-white-quads-300px.jpg)

四角形ではなくダイヤ。


できるだけ多くのオーバースペース (ピクセルが処理される回数) を制限するために、2つの四角形を回転させて重なりが小さくなるようにしました。

### <a name="adding-clouds"></a>クラウドの追加

1つのボリューム内の射線の回転から、クラウドをシミュレートするためにできるだけ多くのパーティクルを描画するなど、さまざまな方法で、容量の感覚を取得できます。 リアルタイムの光の回転はコストが高く、作成が困難になってきました。そのため、最初にゲームでフォレストをレンダリングするためのメソッドを使用してなりすましシステムを構築しようとしました。これは、カメラに面しているツリーの2D イメージを多数備えています。 ゲームでこの操作を行うと、カメラのテクスチャを描画して、回転させたり、すべてのイメージを保存したり、各ビルボードカードの実行時に、ビューの方向に一致する画像を選択したりすることができます。 これは、イメージがホログラムである場合にも機能しません。 左目と右目の違いによって、より高い解像度が必要になるようになります。または、単純、エイリアス、または反復的に表示されます。

2回目の試行では、できるだけ多くのパーティクルを使用しようとしました。 シーンに追加する前に、パーティクルを描画してぼかしを加算したときに最適なビジュアルが得られました。 このアプローチに関する一般的な問題は、一度に描画できるパーティクルの数と、60 fps を維持しながらカバーされる画面領域の量に関連していました。 このクラウドを実現するために生成されたイメージをぼかすことは、通常、非常にコストのかかる操作でした。

![テクスチャを使用しない場合、雲は2% の不透明度で表示されます。](images/clouds-without-texture-300px.jpg)

テクスチャを使用しない場合、雲は2% の不透明度で表示されます。



さらに多くのものが含まれているので、複数の四角形を相互に並べて、同じピクセルの網掛けを繰り返すことになります。 Galaxy の中央では、同じピクセルに何百もの四角形が含まれており、全画面表示が完了すると、非常にコストがかかりました。

全画面表示のクラウドを使用して、その効果をぼかすことは、それほど問題にはなりませんでした。その代わりに、ハードウェアで私たちの作業を行うことにしました。

### <a name="a-bit-of-context-first"></a>最初は少しコンテキスト

ゲームでテクスチャを使用する場合、テクスチャサイズはそれを使用する領域とほとんど一致しませんが、さまざまな種類のテクスチャフィルターを使用して、グラフィックカードを取得し、テクスチャのピクセルから必要な色を補間することができます ([テクスチャフィルター](https://msdn.microsoft.com/library/dn642451.aspx))。 興味のあるフィルター処理は、近接している4つの近隣ノードを使用して任意のピクセルの値を計算する、[バイリニアフィルター](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)です。

![フィルター処理前の元](images/texture-1.png)

![フィルター処理後の結果](images/texture-2.png)

このプロパティを使用すると、テクスチャを領域に2倍の大きさで描画しようとするたびに、結果がぼかしられることがわかります。

全画面表示ではなく、貴重な時間を無駄にしてしまうのではなく、画面の小さなバージョンにレンダリングします。 次に、このテクスチャをコピーして2倍の量で拡大することで、プロセスの内容をぼかしながら全画面表示に戻ります。

![x3 upscale を完全に解決します。](images/galaxy-resolutions-300px.png)

x3 upscale を完全に解決します。



これにより、元のコストのほんの一部のみを使用してクラウドパーツを取得できるようになりました。 完全な解像度でクラウドを追加するのではなく、ピクセルの 1/64th のみを描画し、テクスチャを完全解像度に引き伸ばすだけです。

![左側には、1 ~ 8 の upscale があります。そして、3 upscale を使用すると、2の累乗が使用されます。](images/stars-upscaled-300px.jpg)

左側には、1 ~ 8 の upscale があります。そして、3 upscale を使用すると、2の累乗が使用されます。


サイズの 1/64th から、1つの場所で完全なサイズに移行しようとしても、グラフィックカードではセットアップで4ピクセルが使用され、より大きな領域に影が付けられ、アイテムが表示されるようになるため、まったく異なる結果になることに注意してください。

次に、小さなカードを使用して完全な解像度の星を追加すると、完全な galaxy が得られます。

![完全解決星を使用した galaxy レンダリングの最終結果](images/full-galaxy-500px.png)

図形を適切に追跡した後、クラウドのレイヤーを追加し、Photoshop で描画したものと一時的なドットを入れ替え、追加の色を追加しました。 結果として、アートチームとエンジニアリングチームの両方が優れていることを天の川しています。これは、CPU に負担をかけることなく、深さ、ボリューム、および運動の目標を達成しました。

![3D の最終的な天の川方法です。](images/final-galaxy-500px.jpg)

3D の最終的な天の川方法です。


### <a name="more-to-explore"></a>詳細を見る

Galaxy エクスプローラーアプリのコードをオープンソース化し、開発者向けに[GitHub](https://github.com/Microsoft/GalaxyExplorer)で利用できるようにしました。

Galaxy エクスプローラーの開発プロセスの詳細については、 [Microsoft HoloLens YouTube チャネル](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)で、過去のすべてのプロジェクト更新を確認してください。

## <a name="about-the-authors"></a>作成者について

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b>は、ソフトウェアエンジニアや凝ったビジュアルです。 彼は、Galaxy エクスプローラーのグラフィックスエンジニアでした。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b>は、さらに多くのパーティクルを対象として、Galaxy エクスプローラーと Fought の3d モデリングチームを管理している最先端のリードと宇宙です。</td>
</tr>
</table>


## <a name="see-also"></a>関連項目
* [GitHub の Galaxy エクスプローラー](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube での Galaxy エクスプローラープロジェクトの更新](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
