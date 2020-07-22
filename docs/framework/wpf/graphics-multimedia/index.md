---
title: グラフィックスとマルチメディア
description: Windows Presentation Foundation (WPF) のメディア機能を検出します。 アプリケーションにグラフィックス、切り替え効果、サウンド、ビデオを追加します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: ba52e78564484f7714ab0035a5e1861766b72bbf
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853687"
---
# <a name="graphics-and-multimedia"></a>グラフィックスとマルチメディア

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、マルチ メディア、ベクター グラフィックス、アニメーション、コンテンツ構成のサポートが提供されるので、開発者はユーザーの関心を引くユーザー インターフェイスやコンテンツを簡単に開発できます。 Visual Studio を使用して、ベクター グラフィックスや複雑なアニメーションを作成し、メディアをアプリケーションに統合できます。

このトピックでは、アプリケーションにグラフィックス、画面切り替え効果、サウンド、ビデオを追加できるようにする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のグラフィックス、アニメーション、メディア機能を紹介します。

> [!NOTE]
> Windows サービスで WPF 型を使用するのは避けることを強くお勧めします。 Windows サービスで WPF 型を使用しようとした場合、サービスが期待どおりに動作しないことがあります。

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 のグラフィックスとマルチメディアの新機能

グラフィックスとアニメーションに関するいくつかの変更点があります。

- レイアウトの丸め

  オブジェクトの端が 1 ピクセル デバイスの中間に位置する場合、DPI に依存しないグラフィックス システムでは、端がぼやけたり半透明になったりするなどのレンダリング アーティファクトが発生することがあります。 以前のバージョンの WPF には、このような場合の処理に役立つピクセル スナップが含まれていました。 Silverlight 2 では、端がピクセル境界全体に位置するように要素を移動する別の方法としてレイアウトの丸めが導入されました。 WPF で <xref:System.Windows.FrameworkElement> の <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> 添付プロパティを使用したレイアウトの丸めがサポートされるようになりました。

- キャッシュ済みコンポジション

  新しい <xref:System.Windows.Media.BitmapCache> と <xref:System.Windows.Media.BitmapCacheBrush> のクラスを使用すると、ビジュアル ツリーの複雑な部分をビットマップとしてキャッシュし、レンダリング時間を大幅に短縮することができます。 ビットマップは、マウス クリックなどのユーザー入力に引き続き応答し、その他の要素上にブラシのように描画できます。

- Pixel Shader 3 のサポート

  WPF 4 は、WPF 3.5 SP1 で導入された <xref:System.Windows.Media.Effects.ShaderEffect> サポートを基に、アプリケーションでピクセル シェーダー (PS) バージョン 3.0 を使用した効果を記述できるようにします。 PS 3.0 のシェーダー モデルは PS 2.0 より洗練されており、サポートされているハードウェア上でより多くのエフェクトを使用できます。

- イージング関数

  イージング関数を使用してアニメーションを強化し、アニメーションの動作をより細かく制御できます。 たとえば、<xref:System.Windows.Media.Animation.ElasticEase> をアニメーションに適用すると、アニメーションに弾むような動作を加えることができます。 詳細については、<xref:System.Windows.Media.Animation> 名前空間のイージング型に関する記事を参照してください。

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>グラフィックスとレンダリング

WPF では、高品質な 2D グラフィックがサポートされます。 ブラシ、ジオメトリ、イメージ、図形、変換などの機能が用意されています。 詳しくは、「[グラフィックス](graphics.md)」をご覧ください。 グラフィカル要素のレンダリングは、<xref:System.Windows.Media.Visual> クラスに基づいています。 画面のビジュアル オブジェクトの構造は、ビジュアル ツリーで表されます。 詳しくは、「[WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)」をご覧ください。

### <a name="2d-shapes"></a>2D シェイプ

WPF には、次の図に示す四角形や楕円のような、一般的に使用されるベクター描画の 2D シェイプのライブラリが用意されています。

![楕円と四角形を示す図。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

これらの固有の WPF シェイプは単なるシェイプではなく、一般的なコントロールに期待されるキーボード入力やマウス入力などの機能の多くを実装するプログラミング可能な要素です。 次の例は、<xref:System.Windows.Shapes.Ellipse> 要素をクリックすることによって発生する <xref:System.Windows.UIElement.MouseUp> イベントの処理方法を示しています。

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

上記の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップとコードビハインドの出力を次の図に示します。

!["楕円をクリックしました" というメッセージ ボックス](./media/index/messagebox-text-output.png)

詳しくは、「 [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)」をご覧ください。 入門用のサンプルについては、「[Shape 要素のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)」をご覧ください。

### <a name="2d-geometries"></a>2D ジオメトリ

WPF で提供される 2D シェイプでは不十分な場合は、WPF のジオメトリとパスのサポートを利用して独自に作成できます。 ジオメトリを使用してシェイプを描画ブラシとして作成し、他の WPF 要素をクリップする方法を次の図に示します。

![シェイプを作成するためのジオメトリの使用方法を示すスクリーンショット。](./media/index/use-geometries-create-shapes.png)

詳しくは、「[ジオメトリの概要](geometry-overview.md)」をご覧ください。 入門用のサンプルについては、「[ジオメトリのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)」をご覧ください。

### <a name="2d-effects"></a>2D 効果

WPF には、さまざまな効果の作成に使用できる 2D クラスのライブラリが用意されています。 WPF の 2D レンダリング機能を使用すると、グラデーション、ビットマップ、描画、ビデオを持つ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を塗りつぶすことができます。また、回転、拡大縮小、傾斜を使用してそれらの要素を操作できます。 WPF のブラシを使用して実現できる多くの効果の例を次の図に示します。

![さまざまな WPF のブラシと描画要素を示す図。](./media/index/brushes-paint-elements.png)

詳しくは、「 [WPF のブラシの概要](wpf-brushes-overview.md)」をご覧ください。 入門用のサンプルについては、「[ブラシのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)」をご覧ください。

<a name="rendering"></a>

## <a name="3d-rendering"></a>3D レンダリング

WPF には、さらに魅力的なレイアウト、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、データの視覚化を実現するために WPF の 2D グラフィックス サポートと統合された一連の 3D レンダリング機能が用意されています。 たとえば、WPF では、次の図に示すように 2D イメージを 3D シェイプのサーフェイスにレンダリングできます。

![異なるテクスチャを持つ 3D シェイプを示すサンプルのスクリーンショット。](./media/index/visual-three-dimensional-shape.png)

詳細については、「[3D グラフィックスの概要](3-d-graphics-overview.md)」を参照してください。 入門用のサンプルについては、[3D ソリッドのサンプル](https://go.microsoft.com/fwlink/?LinkID=159964)をご覧ください。

<a name="animation"></a>

## <a name="animation"></a>アニメーション

アニメーションを使用すると、コントロールや要素を拡大、振動、回転、フェードさせることができ、魅力的なページ遷移なども作成できです。 WPF ではほとんどのプロパティをアニメーション化できるため、ほとんどの WPF オブジェクトをアニメーション化できるだけでなく、WPF を使用して作成するカスタム オブジェクトをアニメーション化することもできます。

![アニメーション キューブのスクリーンショット。](./media/index/animate-custom-objects.png)

詳しくは、「 [アニメーションの概要](animation-overview.md)」をご覧ください。 入門用のサンプルについては、「[アニメーション サンプル ギャラリー](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)」をご覧ください。

<a name="media"></a>

## <a name="media"></a>Media

イメージ、ビデオ、オーディオは、情報とユーザー エクスペリエンスを伝えるメディア リッチな手段です。

### <a name="images"></a>イメージ

アイコン、背景、アニメーションのパーツを含むイメージは、ほとんどのアプリケーションの中核です。 イメージは頻繁に使用する必要があるため、WPF ではさまざまな方法でイメージを処理する機能を公開しています。 その方法の 1 つを次の図に示します。

![スタイル サンプルのスクリーンショット](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

詳しくは、「 [イメージングの概要](imaging-overview.md)」をご覧ください。

### <a name="video-and-audio"></a>ビデオとオーディオ

WPF のグラフィックス機能の中核となる機能は、ビデオやオーディオを含むマルチメディアの処理をネイティブにサポートすることです。 次の例では、メディア プレーヤーをアプリケーションに挿入する方法を示しています。

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement> は、ビデオとオーディオの両方を再生でき、カスタム UI を簡単に作成できる拡張性を備えています。

詳しくは、「[マルチメディアの概要](multimedia-overview.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [アニメーションおよびタイミングに関する「方法」トピック](animation-and-timing-how-to-topics.md)
- [3D グラフィックスの概要](3-d-graphics-overview.md)
- [マルチメディアの概要](multimedia-overview.md)
