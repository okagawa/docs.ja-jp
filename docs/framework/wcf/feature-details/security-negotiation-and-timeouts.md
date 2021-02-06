---
description: 詳細については、「セキュリティネゴシエーションとタイムアウト」を参照してください。
title: セキュリティ ネゴシエーションとタイムアウト
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 50055698f9a9946d0c0110a964cf9ce5b9f4fa28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632439"
---
# <a name="security-negotiation-and-timeouts"></a>セキュリティ ネゴシエーションとタイムアウト

クライアントとサービスが認証されると、Windows Communication Foundation (WCF) は、認証の一部としてサービス資格情報がネゴシエートされるモードをサポートします。 このようなシナリオでは、サービス資格情報をクライアントに反映させるために、クライアントとサービスの間でマルチレッグ交換が発生する可能性があります。 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> プロパティは、マルチレッグ交換の完了に要する時間を制御します。 ただし、このタイムアウトは、実際に、単一の要求 - 応答よりも長い時間が交換にかかる場合のみ適用されます。 単一のラウンド トリップでネゴシエーションが完了する場合、このタイムアウトは適用されません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [方法: 時刻のずれの最大値を設定する](how-to-set-a-max-clock-skew.md)
