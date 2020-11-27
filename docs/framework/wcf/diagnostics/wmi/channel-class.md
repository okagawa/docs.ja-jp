---
title: チャネル クラス
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: a920636e7df9609b12834366b1488c80122f9fca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274232"
---
# <a name="channel-class"></a>チャネル クラス

チャネル  
  
## <a name="syntax"></a>構文  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>メソッド  

 チャネル クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 チャネル クラスには、次のプロパティがあります。  
  
### <a name="localaddress"></a>LocalAddress  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 チャネルのローカル エンドポイント。  
  
### <a name="ref"></a>ref  

 データ型 : Endpoint  
  
 アクセスの種類: 読み取り専用  
  
 チャネルが接続するエンドポイントへの参照。  
  
### <a name="remoteaddress"></a>RemoteAddress  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 チャネルに関連するリモート アドレス。  
  
### <a name="sessionid"></a>SessionId  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 現在のセッション ID (存在する場合)。  
  
### <a name="type"></a>Type  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 チャネルの型。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.ChannelBase>
