---
title: UI オートメーション Grid コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 04f3ee1e01054df6a13ab2391e14a6a7f7274bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180215"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>UI オートメーション Grid コントロール パターンの実装
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、プロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.Provider.IGridProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.GridPattern> コントロール パターンは、子要素のコレクションのコンテナーとして機能するコントロールをサポートするために使用します。 この要素の子には <xref:System.Windows.Automation.Provider.IGridItemProvider> を実装する必要があります。また、この要素の子は、行と列で表現できる 2 次元の論理座標システムで編成しなければなりません。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 Grid コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。  
  
- グリッド座標は 0 から始まり、左上 (ロケールによっては右上) のセルの座標が (0,0) になります。  
  
- セルが空の場合でも、そのセルの <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> プロパティをサポートするために、UI オートメーション要素を返す必要があります。 これが可能なのは、グリッド内の子要素のレイアウトが不調和配列に似ている場合です (次の例を参照)。  
  
 ![不規則なレイアウトを示す Windows エクスプローラー ビュー。](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
空の座標を持つグリッド コントロールの例  
  
- 項目が 1 つのグリッドでも、論理的にグリッドであると見なされる場合は、 <xref:System.Windows.Automation.Provider.IGridProvider> を実装する必要があります。 グリッド内の子項目の数は問題ではありません。  
  
- プロバイダーの実装によっては、非表示の行および列は [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーに読み込まれ、 <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> プロパティおよび <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> プロパティに反映されます。 読み込まれていない場合は、非表示の行および列はカウントされません。  
  
- <xref:System.Windows.Automation.Provider.IGridProvider> はグリッドのアクティブな操作を有効にしないため、 <xref:System.Windows.Automation.Provider.ITransformProvider> を実装してこの機能を有効にする必要があります。  
  
- <xref:System.Windows.Automation.StructureChangedEventHandler> を使用すると、追加、削除、マージされたセルなど、グリッドの構造またはレイアウトの変更をリッスンできます。  
  
- <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> を使用すると、グリッドの項目またはセルの反復処理を追跡できます。  
  
<a name="Required_Members_for_IGridProvider"></a>
## <a name="required-members-for-igridprovider"></a>IGridProvider の必須メンバー  
 IGridProvider インターフェイスの実装時には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|Type|Notes|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Method|なし|  
  
 このコントロール パターンには、関連するイベントがありません。  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - 要求された行座標が より大<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>きい場合、または列の座標が<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - 要求された行または列の座標のいずれかが 0 未満の場合。|  
  
## <a name="see-also"></a>関連項目

- [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](ui-automation-control-patterns-for-clients.md)
- [UI オートメーション GridItem コントロール パターンの実装](implementing-the-ui-automation-griditem-control-pattern.md)
- [UI Automation Tree Overview](ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](use-caching-in-ui-automation.md)
