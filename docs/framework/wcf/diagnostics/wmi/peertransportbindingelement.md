---
description: 詳細については、「PeerTransportBindingElement」を参照してください。
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: b1ca8020f51a5f9b121f7d238d82b9971d13cdd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757333"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement

PeerTransportBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>メソッド  

 PeerTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 PeerTransportBindingElement クラスには、次のプロパティがあります。  
  
### <a name="listenipaddress"></a>ListenIPAddress  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 ピア ノードがメッセージをリッスンする IP アドレスです。  
  
### <a name="port"></a>ポート  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 このバインディングがピア チャネル メッセージを処理するネットワーク インターフェイス ポートです。  
  
### <a name="security"></a>セキュリティ  

 データ型 : PeerSecuritySettings  
  
 アクセスの種類: 読み取り専用  
  
 ピア トランスポートのセキュリティ設定です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
