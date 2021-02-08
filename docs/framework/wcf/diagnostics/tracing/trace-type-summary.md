---
description: '詳細情報: トレースの種類の概要'
title: トレースの種類の概要
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: ebfe9de16766494a6aebe0a8d2501954855dc4df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803218"
---
# <a name="trace-type-summary"></a>トレースの種類の概要

[ソースレベル](xref:System.Diagnostics.SourceLevels) では、さまざまなトレースレベル (重大、エラー、警告、情報、および詳細) を定義すると共に、 `ActivityTracing` トレース境界とアクティビティ転送イベントの出力を切り替えるフラグの説明を提供します。  
  
 また <xref:System.Diagnostics.TraceEventType> 、から出力できるトレースの種類を確認することもでき <xref:System.Diagnostics> ます。  
  
 最も重要な種類を次の表に示します。  
  
|トレースの種類|説明|  
|----------------|-----------------|  
|重大|致命的なエラーまたはアプリケーションのクラッシュ。|  
|エラー|回復可能なエラー。|  
|警告|情報メッセージです。|  
|Information|重大ではない問題。|  
|"詳細"|トレースのデバッグ。|  
|開始|処理の論理単位の開始。|  
|[中断]|処理の論理単位の中断。|  
|再開|処理の論理単位の再開。|  
|Stop|処理の論理単位の停止。|  
|転送|相関 ID の変更。|  
  
 アクティビティは、上記のトレースの種類の組み合わせとして定義されます。  
  
 ローカル (トレース ソース) スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 これは、アクティビティが次の条件を満たす必要があることを意味します。  
  
- アクティビティは、Start トレースによって開始し、Stop トレースによって停止する必要があります。  
  
- Suspend トレースまたは Resume トレースの直前に Transfer トレースが必要です。  
  
- Suspend トレースと Resume トレースが存在する場合、これらのトレースの間にトレースが存在することはできません。  
  
- 上記の条件を満たしている限り、Critical/Error/Warning/Information/Verbose/Transfer の各トレースはいくつでも含めることができます。  
  
 グローバル スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。  
  
`R+`  
  
 R はローカル スコープのアクティビティを表す正規表現です。 これは、次のようになります。  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
