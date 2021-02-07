---
description: '詳細情報: TcpConnectionPoolSettings'
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 927fcba7f94bcbfa80e06479e79bf20986a661e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715198"
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings

TcpConnectionPoolSettings  
  
## <a name="syntax"></a>構文  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>メソッド  

 TcpConnectionPoolSettings クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 TcpConnectionPoolSettings クラスには、次のプロパティがあります。  
  
### <a name="groupname"></a>GroupName  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 バインド要素により使用される接続プールのグループ名。  
  
### <a name="idletimeout"></a>IdleTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 接続が切断されるまでの最大アイドル時間。  
  
### <a name="leasetimeout"></a>LeaseTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 リース操作を完了する必要がある、タイムアウトまでの最大時間。  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 各エンドポイントの発信接続の最大数。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
