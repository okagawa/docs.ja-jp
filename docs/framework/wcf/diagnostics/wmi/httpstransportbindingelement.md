---
description: '詳細情報: HttpsTransportBindingElement'
title: HttpsTransportBindingElement
ms.date: 03/30/2017
ms.assetid: e78aa8c6-b53b-4105-a900-d3e7a39670f2
ms.openlocfilehash: 70fadf136080d865a2738e4b93aa5d7edadc0244
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803205"
---
# <a name="httpstransportbindingelement"></a>HttpsTransportBindingElement

HttpsTransportBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp  
class HttpsTransportBindingElement : HttpTransportBindingElement  
{  
  boolean RequireClientCertificate;  
};  
```  
  
## <a name="methods"></a>メソッド  

 HttpsTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 HttpsTransportBindingElement クラスには、次のプロパティがあります。  
  
### <a name="requireclientcertificate"></a>RequireClientCertificate  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 SSL クライアント認証が必要かどうかを示す値。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
