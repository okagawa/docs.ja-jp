---
description: '詳細情報: SymmetricSecurityBindingElement'
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c158f0bedec91a74b305f359889dd307cff48079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715302"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement

SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>メソッド  

 SymmetricSecurityBindingElement クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  

 SymmetricSecurityBindingElement クラスには、次のプロパティがあります。  
  
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

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
