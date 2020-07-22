---
title: Web およびソケットのアクセス許可
description: WebPermission および SocketPermission クラスから、.NET Framework で System.Net 名前空間を使用するためのインターネット セキュリティを提供するしくみについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: 08ae360e8097f7281631da2a3f9846994dfbf5b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501899"
---
# <a name="web-and-socket-permissions"></a>Web およびソケットのアクセス許可
<xref:System.Net> 名前空間を使用したアプリケーションのインターネット セキュリティは、<xref:System.Net.WebPermission> クラスと <xref:System.Net.SocketPermission> クラスで提供されます。 **WebPermission** クラスは、URI からデータを要求するか、URI をインターネットに提供するアプリケーションの権限を制御します。 **SocketPermission** クラスは、ソケットのホスト、ポート番号、およびトランスポート プロトコルに基づいて、アプリケーションが <xref:System.Net.Sockets.Socket> を使用してローカル ポートでデータを受け入れる権利、または別のアドレスでトランスポート プロトコルを使用してリモート デバイスに接続する権利を制御します。  
  
 使用するアクセス許可クラスは、アプリケーションの種類によって変わります。 <xref:System.Net.WebRequest> とその子孫を使用するアプリケーションでアクセス許可を管理するには、**WebPermission** クラスを使用するようにします。 ソケットレベルのアクセスを使用するアプリケーションでアクセス許可を管理するには、**SocketPermission** クラスを使用するようにします。  
  
 **WebPermission** と **SocketPermission** は、受け入れと接続という 2 つのアクセス許可を定義します。 受け入れは、別のパーティーからの受信接続に応答する権利をアプリケーションに付与します。 接続は、別のパーティーへの接続を開始する権利をアプリケーションに付与します。  
  
 **SocketPermission** インスタンスの場合、受け入れとは、アプリケーションがローカル トランスポート アドレスで受信接続を受け入れ可能であることを意味し、接続とは、アプリケーションが何らかのリモート (またはローカル) トランスポート アドレスに接続できることを意味します。  
  
 **WebPermission** インスタンスの場合、受け入れとは、**WebPermission** が制御する URI を世界にエクスポートできることを意味し、接続とは、アプリケーションがその URI (リモートまたはローカル) にアクセスできることを意味します。  
  
## <a name="see-also"></a>関連項目

- [セキュリティ](../../standard/security/index.md)
- [ネットワーク プログラミングにおけるセキュリティ](security-in-network-programming.md)
