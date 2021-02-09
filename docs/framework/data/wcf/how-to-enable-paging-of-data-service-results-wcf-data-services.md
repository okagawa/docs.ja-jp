---
description: '詳細情報: 方法:データ サービスの結果のページングを有効にする (WCF Data Services)'
title: '方法: データ サービスの結果のページングを有効にする (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 27a2b37f432d906022d06492b2f687681d9b9ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765335"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>方法: データ サービスの結果のページングを有効にする (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Data Services では、データ サービス クエリによって返されるエンティティの数を制限できます。 ページ制限は、サービスの初期化時に呼び出されるメソッドで定義され、エンティティ セットごとに設定できます。  
  
 ページングが有効である場合、フィードの最終的なエントリには、データの次のページへのリンクが含まれます。 詳細については、「[データ サービスの構成](configuring-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックでは、返された `Customers` エンティティ セットおよび `Orders` エンティティ セットのページングを有効にするためにデータ サービスを変更する方法について説明します。 このトピックの例では、Northwind サンプル データ サービスを使用します。 このサービスは、[WCF Data Services クイック スタート](quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>返された Customer エンティティ セットおよび Orders エンティティ セットのページングを有効化する方法  
  
- データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>関連項目

- [遅延コンテンツの読み込み](loading-deferred-content-wcf-data-services.md)
- [方法: ページングされた結果を読み込む](how-to-load-paged-results-wcf-data-services.md)
