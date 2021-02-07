---
description: '詳細情報: AsymmetricSecurityBindingElement'
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 25d0ac205491e9ce27c59d3a0670d1e4a3150e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757944"
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement

AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>メソッド  

 AsymmetricSecurityBindingElement クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  

 AsymmetricSecurityBindingElement クラスには、次のプロパティがあります。  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 このバインディングのメッセージの暗号化と署名の命令。  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 バインディングで署名の確認が必要かどうか。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
