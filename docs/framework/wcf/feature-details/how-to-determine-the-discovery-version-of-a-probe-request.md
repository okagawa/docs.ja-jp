---
description: '詳細については、「方法: プローブ要求の探索バージョンを確認する」を参照してください。'
title: '方法: Probe 要求の探索バージョンを特定する'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: c41283cb84d75dd2dbf7e86da0dec075ab8b6635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793793"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>方法: Probe 要求の探索バージョンを特定する

探索プロキシでは、異なる探索バージョンを使用する複数の探索エンドポイントを公開する場合があります。 UDP マルチキャストプローブ要求がプロキシに到着すると、プロキシはマルチキャスト抑制メッセージで応答する必要があります。 このためには、要求の探索バージョンを把握している必要があります。

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Probe 要求の探索バージョンを特定するには

プローブ要求に応答するメソッド (たとえば) では、 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> 次のコードに示すように、静的プロパティを使用してを検索し <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> ます。

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [探索プロキシの実装](implementing-a-discovery-proxy.md)
