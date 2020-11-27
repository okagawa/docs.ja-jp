---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 2de417e4a4f5c6197551c1408da6907e2fa7c635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269003"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings

PeerSecuritySettings  
  
## <a name="syntax"></a>構文  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a>メソッド  

 PeerSecuritySettings クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 PeerSecuritySettings クラスには、次のプロパティがあります。  
  
### <a name="mode"></a>モード  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 このバインディングで構成されたエンドポイントによって、メッセージ レベルおよびトランスポート レベルのセキュリティが使用されているかどうかを示します。  
  
### <a name="transport"></a>トランスポート  

 データ型 : PeerTransportSecuritySettings  
  
 アクセスの種類: 読み取り専用  
  
 トランスポートのセキュリティ設定です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.PeerSecuritySettings>
