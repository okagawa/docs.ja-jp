---
title: 'コア通信: TCP トランスポート チャネル'
ms.date: 03/30/2017
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
ms.openlocfilehash: c9b2b31aaffccaae442f4444f69538245a813570
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96277336"
---
# <a name="core-communications-tcp-transport-channels"></a>コア通信: TCP トランスポート チャネル

ここでは、TCP トランスポート チャネル によって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|指定したソケットのリモート エンドポイントは、割り当てられたタイムアウト時間内に終了要求に応答しませんでした。 この原因としては、リモート エンドポイントが Receive 操作から EOF 信号 (NULL) を受信した後に Close を呼び出していない可能性があります。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|
