---
description: '詳細情報: 方法:EntityConnection の接続文字列を作成する'
title: '方法: EntityConnection の接続文字列を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: 760ed9d1f362e08135586a56a6b900afcd2b13bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650834"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a>方法: EntityConnection の接続文字列を作成する

このトピックでは、<xref:System.Data.EntityClient.EntityConnection> を作成する方法について説明します。  
  
### <a name="to-run-the-code-in-this-example"></a>この例のコードを実行するには  
  
1. [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。 詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。  
  
2. アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>例  

 次の例では、基になるプロバイダーの <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> を初期化した後、<xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> オブジェクトを初期化して、このオブジェクトを <xref:System.Data.EntityClient.EntityConnection> のコンストラクターに渡しています。  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a>関連項目

- [方法: オブジェクト コンテキストで EntityConnection を使用する](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))」
- [Entity Framework 用の EntityClient プロバイダー](entityclient-provider-for-the-entity-framework.md)
