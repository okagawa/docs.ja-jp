---
description: '詳細情報: 方法:Entity Framework プロバイダーでフィードをカスタマイズする (WCF Data Services)'
title: '方法: Entity Framework プロバイダーでフィードをカスタマイズする (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: b2d2432065ee0982822d0f332744f988d80add12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765673"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>方法: Entity Framework プロバイダーでフィードをカスタマイズする (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Data Services では、データ サービス応答の Atom シリアル化をカスタマイズして、AtomPub プロトコルで定義されている未使用の要素にエンティティのプロパティをマップできます。 このトピックでは、Entity Framework を使用して、.edmx ファイルで定義されているデータ モデルのエンティティ型のマッピング属性を定義する方法について説明します。 詳細については、「[フィードのカスタマイズ](feed-customization-wcf-data-services.md)」を参照してください。  
  
 このトピックでは、ツールによって生成された .edmx file ファイルを手動で変更します (このファイルには、データ モデルが含まれます)。 エンティティ デザイナーではデータ モデルへの拡張がサポートされていないので、このファイルは手動で変更する必要があります。 Entity Data Model ツールによって生成される .edmx ファイルの詳細については、「[.edmx ファイルの概要 (Entity Framework)](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))」を参照してください。 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスは、「[WCF Data Services クイックスタート](quickstart-wcf-data-services.md)」を完了すると作成されます。  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Northwind.edmx ファイルを手動で変更してフィードのカスタマイズ属性を追加するには  
  
1. **ソリューション エクスプローラー** で `Northwind.edmx` ファイルを右クリックして、 **[プログラムから開く]** をクリックします。  
  
2. **[Northwind.edmx を開くアプリケーションの選択]** ダイアログ ボックスで、 **[XML エディター]** を選択し、 **[OK]** をクリックします。  
  
3. `ConceptualModels` 要素を見つけて、フィードのカスタマイズ マッピング属性を含む次の要素で既存の `Customers` エンティティ型を置き換えます。  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4. 変更を保存して Northwind.edmx ファイルを閉じます。  
  
5. (オプション) Northwind.edmx ファイルを右クリックして、 **[カスタム ツールの実行]** をクリックします。  
  
     オブジェクト レイヤー ファイルが再生成されます。このファイルが必要になる場合があります。  
  
6. プロジェクトを再コンパイルします。  
  
## <a name="example"></a>例  

 前の例では、URI `http://myservice/Northwind.svc/Customers('ALFKI')` に次の結果が返されます。  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>関連項目

- [Entity Framework プロバイダー](entity-framework-provider-wcf-data-services.md)
