---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 806066a8845068413d2a52c78878f76b5f5fa34f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250373"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement

OneWayBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>メソッド  

 OneWayBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 OneWayBindingElement クラスには、次のプロパティがあります。  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  

 データ型 : ChannelPoolSettings  
  
 アクセスの種類: 読み取り専用  
  
 チャネル プールの設定。  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 許可されるチャネルの最大数。  
  
### <a name="packetroutable"></a>PacketRoutable  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 パケットがルーティング可能かどうかを示す値。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
