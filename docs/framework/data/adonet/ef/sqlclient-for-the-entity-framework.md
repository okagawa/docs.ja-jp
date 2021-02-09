---
description: '詳細情報: Entity Framework 用 SqlClient'
title: Entity Framework 用 SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: eba5602c13f66d1ee4404bbc27035304e34c1cd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673129"
---
# <a name="sqlclient-for-the-entity-framework"></a>Entity Framework 用 SqlClient

このセクションでは、.NET Framework Data Provider for SQL Server (SqlClient) について説明します。これによって、Microsoft SQL Server 上で Entity Framework が機能できるようになります。  
  
## <a name="provider-schema-attribute"></a>Provider スキーマ属性  

 `Provider` は、ストア スキーマ定義言語 (SSDL) の `Schema` 要素の属性です。  
  
 SqlClient を使用するには、文字列 "System.Data.SqlClient" を `Provider` 要素の `Schema` 属性に割り当てます。  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken スキーマ属性  

 `ProviderManifestToken` は、SSDL の`Schema` 要素の必須の属性です。 このトークンは、オフライン シナリオ用のプロバイダー マニフェストを読み込むために使用されます。 `ProviderManifestToken` 属性の詳細については、「[Schema 要素 (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl)」を参照してください。  
  
 SqlClient は、SQL Server の各バージョンのデータ プロバイダーとして使用できます。 これらのバージョンでは機能が異なります。 たとえば、SQL Server 2000 では、SQL Server 2005 で導入された `varchar(max)` 型および `nvarchar(max)` 型はサポートされません。  
  
 SqlClient は、SQL Server の各バージョンに対応する次のプロバイダー マニフェスト トークンを生成し、受け取ります。  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
> Visual Studio 2010 以降では、[ADO.NET Entity Data Model ツール](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))によって SQL Server 2000 がサポートされません。  
  
## <a name="provider-namespace-name"></a>プロバイダーの名前空間名  

 すべてのプロバイダーで名前空間を指定する必要があります。 このプロパティによって、型や関数など、プロバイダーが特定のコンストラクターに使用するプレフィックスを Entity Framework に通知できます。 SqlClient プロバイダー マニフェストの名前空間は `SqlServer` です。 名前空間の詳細については、「[名前空間](./language-reference/namespaces-entity-sql.md)」を参照してください。  
  
## <a name="types"></a>型  

 Entity Framework 用の SqlClient プロバイダーは、概念モデルの型と SQL Server 型の間のマッピング情報を提供します。 詳細については、「[Entity Framework 用 SqlClient の型](sqlclient-for-ef-types.md)」を参照してください。  
  
## <a name="functions"></a>関数  

 Entity Framework 用の SqlClient プロバイダーは、プロバイダーがサポートする関数の一覧を定義します。 サポートされている関数の一覧については、「[Entity Framework 用 SqlClient 関数](sqlclient-for-ef-functions.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [Entity Framework 用 SqlClient 関数](sqlclient-for-ef-functions.md)  
  
 [Entity Framework 型用 SqlClient](sqlclient-for-ef-types.md)  
  
 [Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>関連項目

- [Entity SQL 言語](./language-reference/entity-sql-language.md)
- [言語リファレンス](./language-reference/index.md)
- [Entity Framework 用の SqlClient プロバイダーの既知の問題](sqlclient-for-the-entity-framework.md)
