---
description: '詳細情報: ChannelPoolSettings'
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: b08c5483e7a0c918393795b4608b9eef16b18341
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757684"
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings

ChannelPoolSettings  
  
## <a name="syntax"></a>構文  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>メソッド  

 ChannelPoolSettings クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 ChannelPoolSettings クラスには、次のプロパティがあります。  
  
### <a name="idletimeout"></a>IdleTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 接続が切断されるまでの最大アイドル時間。  
  
### <a name="leasetimeout"></a>LeaseTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 リース操作の完了がタイムアウトするまでの最大時間。  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 各エンドポイントでの送信チャネルの最大数。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
