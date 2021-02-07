---
description: 詳細については、「WCF サービスホストの自動起動の制御」を参照してください。
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f0e9a4e79a403920c0bc6a512b30fb038b2aa1f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677393"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF サービス ホストの自動起動の制御

複数のプロジェクトを含む同じ Visual Studio ソリューションで別のプロジェクトをデバッグするときに、WCF サービスライブラリプロジェクトの Windows Communication Foundation (WCF) サービスホスト (WcfSvcHost.exe) の自動起動機能を制御できます。  
  
 これを行うには、 **ソリューションエクスプローラー** で Wcf サービスプロジェクトを右クリックし、[ **プロパティ**] をクリックして、[ **wcf オプション** ] タブをクリックします。既定では、[ **同じソリューションで別のプロジェクトをデバッグするときに WCF サービスホストを開始する** ] チェックボックスがオンになっています。 このチェックボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの WCF サービスホストが起動されないようにすることができます。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
- WCF サービスライブラリプロジェクト。  
  
- シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
- ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
- 配信サービス ライブラリ プロジェクト  
  
## <a name="see-also"></a>関連項目

- [WCF サービス ホスト (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
