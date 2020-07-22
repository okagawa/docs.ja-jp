---
title: AsyncCallback デリゲートの使用による非同期操作の終了
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: 8766e64c52688e820d0eb6a259e39926555d97bd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276350"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>AsyncCallback デリゲートの使用による非同期操作の終了
非同期操作の結果の待機中に、他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックする必要はありません。 次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、手順の実行を継続します。  
  
- <xref:System.AsyncCallback> デリゲートを使用し、個別のスレッドで非同期操作の結果を処理します。 このトピックでは、この方法のデモが実行されます。  
  
- 非同期操作の **Begin**_OperationName_ メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.IsCompleted%2A> プロパティを使用して、その操作が完了したかどうかを判断します。 この方法のデモを実行する例については、「[非同期操作のステータスのポーリング](polling-for-the-status-of-an-asynchronous-operation.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム (DNS) 情報を取得するために、<xref:System.Net.Dns> クラスの非同期メソッドを使用してデモを実行します。 この例では、`ProcessDnsInformation` メソッドを参照する <xref:System.AsyncCallback> デリゲートを作成します。 このメソッドは、DNS 情報に対する非同期要求ごとに 1 回呼び出されます。  
  
 ユーザー指定のホストは、<xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> パラメーターに渡されます。 複雑な状態オブジェクトの定義と使用に関するデモを実行する例については、「[AsyncCallback デリゲートおよび状態オブジェクトの使用](using-an-asynccallback-delegate-and-state-object.md)」を参照してください。  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>参照

- [イベント ベースの非同期パターン (EAP)](event-based-asynchronous-pattern-eap.md)
- [イベントベースの非同期パターンの概要](event-based-asynchronous-pattern-overview.md)
- [IAsyncResult を使用した非同期メソッドの呼び出し](calling-asynchronous-methods-using-iasyncresult.md)
- [AsyncCallback デリゲートおよび状態オブジェクトの使用](using-an-asynccallback-delegate-and-state-object.md)
