---
description: '詳細情報: 方法:関連エンティティを読み込む (WCF Data Services)'
title: '方法: 関連エンティティを読み込む (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 004e52b17c399abe8564dd069dd251d7baf296cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765257"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>方法: 関連エンティティを読み込む (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

関連付けられたエンティティを WCF Data Services で読み込む必要がある場合、<xref:System.Data.Services.Client.DataServiceContext> クラスの <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> メソッドを使用できます。 <xref:System.Data.Services.Client.DataServiceQuery%601> で <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用して、関連エンティティが同じクエリ応答で集中的に読み込むよう要求することもできます。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスは、「[WCF Data Services クイックスタート](quickstart-wcf-data-services.md)」を完了すると作成されます。  
  
## <a name="example"></a>例  

 次の例は、返される各 `Customer` インスタンスに関連付けられた `Orders` を明示的に読み込む方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>例  

 次の例は、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用して、クエリによって返される `Order Details` に属する `Orders` を返す方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>関連項目

- [データ サービスに対するクエリ](querying-the-data-service-wcf-data-services.md)
