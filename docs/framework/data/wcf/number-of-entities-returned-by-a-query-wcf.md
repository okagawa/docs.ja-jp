---
description: '詳細情報: 方法:クエリで返されたエンティティの数を確認する (WCF Data Services)'
title: '方法: クエリで返されたエンティティの数を確認する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: f8eb305bc515d1d69025ce3bcd0a6a9f3baf8232
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794989"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>方法: クエリで返されたエンティティの数を確認する (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Data Services を使用すると、クエリ URI によって指定されたエンティティ セット内のエンティティの数を確認できます。 この数は、クエリ結果と一緒に、または整数値として含まれます。 詳細については、「[データ サービスに対するクエリ](querying-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスは、「[WCF Data Services クイックスタート](quickstart-wcf-data-services.md)」を完了すると作成されます。  
  
## <a name="example"></a>例  

 次の例では、<xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> メソッドを呼び出した後でクエリを実行します。 <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> プロパティが、`Customers` エンティティ セット内のエンティティの数を返します。  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>例  

 次の例では、<xref:System.Linq.Enumerable.Count%2A> エンティティ セット内のエンティティの数である整数値のみを返す `Customers` メソッドを呼び出します。  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>関連項目

- [データ サービスに対するクエリ](querying-the-data-service-wcf-data-services.md)
