---
title: データ サービス プロバイダー (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: eb7d92b1605c6ced8319e0372c8471cd4e388cb8
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569240"
---
# <a name="data-services-providers-wcf-data-services"></a>データ サービス プロバイダー (WCF Data Services)
WCF Data Services では、Open Data Protocol (OData) フィードとしてデータを公開する複数のプロバイダー モデルがサポートされています。 このトピックでは、データ ソースに最適な WCF Data Services プロバイダーを選択するための情報を示します。  
  
## <a name="data-source-providers"></a>データ ソース プロバイダー  
 WCF Data Services では、データ サービスのデータ モデルを定義する以下のプロバイダーがサポートされています。  
  
|プロバイダー|説明|  
|--------------|-----------------|  
|Entity Framework プロバイダー|このプロバイダーは、ADO.NET Entity Framework を使用して、リレーショナル データにマップするデータ モデルを定義することによってデータ サービスでリレーショナル データを使用します。 データ ソースとしては、SQL Server 以外にも、Entity Framework をサポートするサードパーティ プロバイダーのある任意のデータ ソースを使用できます。 SQL Server データベースなどのリレーショナル データ ソースの場合は、Entity Framework プロバイダーを使用してください。 詳しくは、「[Entity Framework プロバイダー](entity-framework-provider-wcf-data-services.md)」をご覧ください。|  
|リフレクション プロバイダー|このプロバイダーは、リフレクションを使用して、<xref:System.Linq.IQueryable%601> インターフェイスのインスタンスとして公開できる既存のデータ クラスに基づいてデータ モデルを定義できます。 <xref:System.Data.Services.IUpdatable> インターフェイスを実装することによって更新できます。 実行時に定義される静的なデータ クラス (LINQ to SQL や型指定された DataSet によって生成されたデータ クラスなど) がある場合は、このプロバイダーを使用してください。 詳細については、「[リフレクション プロバイダー](reflection-provider-wcf-data-services.md)」を参照してください。|  
|カスタム データ サービス プロバイダー|WCF Data Services には、遅延バインディング データ型に基づいてデータ モデルを動的に定義できるプロバイダーのセットが含まれています。 公開されるデータが不明な場合、アプリケーションを設計中の場合、または Entity Framework プロバイダーやリフレクション プロバイダーでは不十分な場合には、これらのインターフェイスを実装する必要があります。 詳しくは、「[カスタム データ サービス プロバイダー](custom-data-service-providers-wcf-data-services.md)」をご覧ください。|  
  
## <a name="other-data-service-providers"></a>その他のデータ サービス プロバイダー  
 WCF Data Services には、次の追加のデータ サービス プロバイダーがあり、他のいずれかのプロバイダーを使用して定義されたデータ ソースのパフォーマンスが向上します。  
  
|プロバイダー|説明|  
|--------------|-----------------|  
|ストリーミング プロバイダー|このプロバイダーを使用すると、WCF Data Services を使用してバイナリ ラージ オブジェクト データ型を公開できます。 ストリーミング プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスを実装することによって作成されます。 このプロバイダーは、任意のデータ ソース プロバイダーと共に実装できます。 詳細については、「[ストリーミング プロバイダー](streaming-provider-wcf-data-services.md)」を参照してください。|  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](defining-wcf-data-services.md)
- [データ サービスの構成](configuring-the-data-service-wcf-data-services.md)
- [データ サービスのホスティング](hosting-the-data-service-wcf-data-services.md)
