---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 921a880dad0d77558a70dff8a09f75c25a3cbb8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262282"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior

ServiceMetadataBehavior  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a>メソッド  

 ServiceMetadataBehavior クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 ServiceMetadataBehavior クラスには、次のプロパティがあります。  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 サービスがメタデータ要求をリダイレクトする場所を設定します。  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 `HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。  
  
### <a name="httpgeturl"></a>HttpGetUrl  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 `HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
