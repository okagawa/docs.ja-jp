---
description: 詳細については、「メタデータエンドポイントの公開」をご覧ください。
title: メタデータ エンドポイントを公開する
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 8204a62413e09c0fbc6effaae1fd752aee397147
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726677"
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
