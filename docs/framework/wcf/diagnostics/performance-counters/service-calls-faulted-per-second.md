---
title: 'サービス : 1 秒あたりの失敗した呼び出し'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: d9db777d17de51caff74610d099a79228df1f6d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252947"
---
# <a name="service-calls-faulted-per-second"></a>サービス : 1 秒あたりの失敗した呼び出し

カウンター名 : 1 秒あたりの失敗した呼び出し。  
  
## <a name="description"></a>Description  

 このサービスの呼び出しのうち、エラーを返したものの 1 秒あたりの回数です。  
  
 このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Windows Communication Foundation (WCF) アプリケーションでは、サービスメソッドは SOAP エラーメッセージを使用して処理エラー情報を通信します。 SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。 SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。  
  
## <a name="see-also"></a>関連項目

- [コントラクトおよびサービスのエラーの指定と処理](../../specifying-and-handling-faults-in-contracts-and-services.md)
