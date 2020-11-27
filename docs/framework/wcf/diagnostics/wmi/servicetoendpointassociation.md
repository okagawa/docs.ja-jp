---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 6e20556541b1aa48e7dfc6a8cde97e1bc477457e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273946"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation

エンドポイントにサービスを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>メソッド  

 ServiceToEndpointAssociation クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 ServiceToEndpointAssociation クラスには、次のプロパティがあります。  
  
### <a name="ref"></a>ref  

 データ型 : Service  
  
 アクセスの種類: 読み取り専用  
修飾子: キー  
  
 エンドポイントに関連付けられるサービス。  
  
### <a name="ref"></a>ref  

 データ型 : Endpoint  
  
 アクセスの種類: 読み取り専用  
修飾子: キー  
  
 サービスに関連付けられるエンドポイント。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|
