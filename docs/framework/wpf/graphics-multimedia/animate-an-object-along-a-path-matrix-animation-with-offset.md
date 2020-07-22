---
title: '方法: パスに沿ってオブジェクトをアニメーション化する (オフセット累積による行列アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453105"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>方法: パスに沿ってオブジェクトをアニメーション化する (オフセット累積による行列アニメーション)
この例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> クラスを使用して、パスに沿ってオブジェクトをアニメーション化し、そのアニメーションを繰り返すたびにオフセット値を累積する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> オブジェクトを使用して、ボタンに適用される <xref:System.Windows.Media.MatrixTransform> の <xref:System.Windows.Media.MatrixTransform.Matrix%2A> プロパティをアニメーション化します。 その結果、ボタンは曲線状のパスに沿って移動します。  
  
 また、この例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> プロパティを `true` に設定することにより、アニメーションの繰り返しに応じて、アニメーション化された行列のオフセットを累積します。 オフセットが累積されるので、アニメーションが繰り返されたとき、ボタンは開始位置にリセットされるのではなく、画面を横切ってさらに移動します。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> プロパティを指定すると繰り返しの間ずっとオフセット値が累積しますが、回転値は累積されないことに注意してください。 回転値を累積させるには、アニメーションの <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> と <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> プロパティを `true` に設定します。  
  
 サンプル全体については、「[パス アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)」を参照してください。 オフセットを累積せず、パスに沿って <xref:System.Windows.Media.Matrix> 値をアニメーション化する方法を示した例については、「[パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)](how-to-animate-an-object-along-a-path-matrix-animation.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [パス アニメーションに関する「方法」トピック](path-animation-how-to-topics.md)
