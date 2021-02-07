---
description: 詳細については、「探索のバージョン管理」をご覧ください。
title: 探索機能のバージョン指定
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 075fefce0477810336c8b857343984070ed89b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743188"
---
# <a name="discovery-versioning"></a>探索機能のバージョン指定

ここでは、新しい探索機能の実装の概要について簡単に説明します。 使用する探索バージョンを選択する方法の概要も示します。

## <a name="discovery-versioning"></a>探索機能のバージョン指定

探索機能は、WS_Discovery プロトコルの 3 つのバージョンをサポートします。 探索 API を使用すると、使用するプロトコルのバージョンを選択できます。 このドキュメントでは、バージョン指定に関連する設定について簡単に説明します。

次の Discovery クラスには <xref:System.ServiceModel.Discovery.DiscoveryVersion> プロパティがあり、コンストラクターで <xref:System.ServiceModel.Discovery.DiscoveryVersion> 引数を受け取ります。

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>

### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion.WSDiscoveryApril2005

を <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> コンストラクターパラメーターとして指定すると、実装では WS-Discovery プロトコルの April2005 バージョンが使用されます。 このバージョンは、WS-Discovery プロトコル仕様の発行済みバージョンに対応します。 このバージョンは、WS-Discovery の April2005 バージョンを利用しているレガシ アプリケーションとの相互運用時に使用する必要があります。

### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion.WSDiscovery11

Api で使用される既定の探索バージョンは <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11> です。 これは、現在標準化されている WS-Discovery プロトコルのバージョンです。

## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion.WSDiscoveryCD1

コンストラクターのパラメーターとして <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> を使用することで、WS-Discovery プロトコルの Committee Draft 1 バージョンが実装で使用されます。 このバージョンのプロトコルは、WS-Discovery プロトコルの CD1 バージョンを利用している実装との相互運用時に使用する必要があります。

## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>単一のサービス ホスト上にある異なる探索バージョン用の複数の UDP 探索エンドポイントのサポート

単一のサービス ホスト上にある、異なる探索バージョン用の複数の UDP 探索エンドポイントを公開する場合があります。 このような場合、UDP 探索エンドポイントごとに一意のアドレスを指定する必要があります。 次の例は、その方法を示したものです。

```csharp
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);

newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionApril2005");

serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);
```
