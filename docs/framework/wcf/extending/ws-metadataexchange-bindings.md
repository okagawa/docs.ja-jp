---
title: WS-MetadataExchange のバインディング
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 94f0ba602cd1f58f5491a44a64e24be8ea52895b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293989"
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange のバインディング

ここでは、既定のメタデータ交換バインディングを各種のトランスポート用に構築する方法を説明します。  
  
## <a name="the-default-bindings"></a>既定のバインディング  
  
|既定のバインディング名|バインディングを構築する方法|  
|--------------------------|------------------------------------|  
|mexHttpBinding|トランスポート レベルのセキュリティが無効な <xref:System.ServiceModel.WSHttpBinding>。|  
|mexHttpsBinding|トランスポート レベルのセキュリティをサポートする <xref:System.ServiceModel.WSHttpBinding>。|  
|mexNamedPipeBinding|<xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。|  
|mexTcpBinding|<xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。|
