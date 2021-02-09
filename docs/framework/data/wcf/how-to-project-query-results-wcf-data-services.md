---
description: '詳細情報: 方法:クエリ結果を射影する (WCF Data Services)'
title: '方法: クエリ結果を射影する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
ms.openlocfilehash: a851176e5f97e31d2e8d9ac62c720d04df4ddc37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765114"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>方法: クエリ結果を射影する (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

射影は、エンティティの特定のプロパティのみが応答で返されるように指定することにより、クエリによって返されるデータの量を減らすためのメカニズムです。 WCF Data Services クエリの結果に射影を実行するには、`$select` クエリ オプションを使用するか、LINQ クエリで [select](../../../csharp/language-reference/keywords/select-clause.md) 句 (Visual Basic の場合は [Select](../../../visual-basic/language-reference/queries/select-clause.md)) を使用します。 詳細については、「[データ サービスに対するクエリ](querying-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスは、「[WCF Data Services クイックスタート](quickstart-wcf-data-services.md)」を完了すると作成されます。  
  
## <a name="example"></a>例  

 次の例では、アドレス特有のプロパティと Identity プロパティのみを含む新しい CustomerAddress 型に Customer エンティティを射影する LINQ クエリを示します。 この `CustomerAddress` クラスはクライアントで定義され、クライアント ライブラリがエンティティ型として認識できるように属性化されています。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>例  

 次の例では、返された Customers エンティティを、Identity プロパティは含まずにアドレス特有のプロパティのみを含む新しい CustomerAddressNonEntity 型に射影する LINQ クエリを示します。 この `CustomerAddressNonEntity` クラスはクライアントで定義され、エンティティ型としては属性化されません。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>例  

 次の例では、前の例で使用した `CustomerAddress` 型と `CustomerAddressNonEntity` 型の定義を示します。  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
