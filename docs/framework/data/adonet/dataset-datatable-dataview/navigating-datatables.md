---
description: '詳細情報: DataTable の移動'
title: DataTable の移動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 0564af241adc082ef1b736f2e4a561328fbcc976
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651783"
---
# <a name="navigating-datatables"></a>DataTable の移動

<xref:System.Data.DataTableReader> は、1 つ以上の <xref:System.Data.DataTable> オブジェクトの内容を、読み取り専用、前方参照専用の 1 つ以上の結果セットとして取得します。  
  
 <xref:System.Data.DataTableReader> メソッドの呼び出しにより DataTableReader を作成した場合、<xref:System.Data.DataSet.CreateDataReader%2A> に複数の結果セットが含まれる場合があります。 結果セットが複数ある場合、<xref:System.Data.DataTableReader.NextResult%2A> メソッドは、カーソルを次の結果セットに移動します。 これは前方参照専用です。 前の結果セットに戻ることはできません。  
  
## <a name="example"></a>例  

 次の例では、`TestConstructor` メソッドで 2 つの <xref:System.Data.DataTable> インスタンスを作成します。 <xref:System.Data.DataTableReader> クラスを対象としたこのコンストラクターを示すために、この例では、2 つの **DataTable** が含まれる配列に基づいた新しい **DataTableReader** を作成し、単純な操作を実行して、最初の数列の内容をコンソール ウィンドウに表示します。  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [DataTableReaders](datatablereaders.md)
- [ADO.NET の概要](../ado-net-overview.md)
