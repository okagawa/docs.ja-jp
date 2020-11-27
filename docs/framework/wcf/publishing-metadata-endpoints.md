---
title: メタデータ エンドポイントを公開する
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 5be27a72c87d95e36a5b283e7930ba0a5191a5a1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249762"
---
# <a name="publishing-metadata-endpoints"></a>メタデータ エンドポイントを公開する

Windows Communication Foundation (WCF) サービスは、1つまたは複数のメタデータエンドポイントを公開することによってメタデータを公開します。 サービス メタデータを公開すると、そのメタデータで WS-MetadataExchange (MEX) や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。 メタデータのエンドポイントは、アドレス、バインディング、およびコントラクトを持つ他のサービス エンドポイントに似ており、構成またはコードを使用してサービス ホストに追加できます。 メタデータ エンドポイントの公開を有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> サービス動作をサービスに追加する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [方法: 構成ファイルを使用してサービスのメタデータを公開する](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 クライアントがクエリ文字列を使用して WS-MetadataExchange または HTTP/GET 要求を使用してメタデータを取得できるように、メタデータを公開するように WCF サービスを構成する方法を示し `?wsdl` ます。  
  
 [方法: コードを使用してサービスのメタデータを公開する](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 WCF サービスのメタデータ公開をコードで有効にし、クライアントがクエリ文字列を使用して WS-MetadataExchange または HTTP/GET 要求を使用してメタデータを取得できるようにする方法を示し `?wsdl` ます。  
  
## <a name="see-also"></a>関連項目

- [メタデータの公開](./feature-details/publishing-metadata.md)
