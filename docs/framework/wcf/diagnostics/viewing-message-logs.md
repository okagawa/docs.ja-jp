---
title: メッセージ ログを参照する
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: c8313b14a45051b7828a1ab223a3da63b2e7a153
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291155"
---
# <a name="viewing-message-logs"></a>メッセージ ログを参照する

ここでは、メッセージ ログの表示方法について説明します。  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>サービス トレース ビューアーでのメッセージ ログの表示  

 メッセージは、WCF によって処理されるときに変換されます。 そのため、ログ記録されたメッセージは、ログ記録された時点でのメッセージの内容を反映しているにすぎず、ネットワーク上での内容ではありません。  
  
 メッセージ ログの出力はメッセージの転送形式とは関係がないため、メッセージ ログは常にデコードされたメッセージを出力します。 メッセージ ログが適切に設定されていれば、すべてのログ メッセージはプレーンテキストになります。 たとえば、ログ メッセージの形式 (プレーンテキスト) は、バイナリ メッセージ エンコーダーの使用には影響されません。  
  
 XmlWriterTraceListener の出力は、一連の XML フラグメントを含んだファイルです。 このファイルは有効な XML ファイルではないことに注意してください。 メッセージログファイルを表示するには、 [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) を使用することをお勧めします。 このツールの使用方法の詳細については、「 [サービストレースビューアーを使用した相関トレースの表示とトラブルシューティング](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)」を参照してください。  
  
 サービストレースビューアーでは、メッセージは [ **メッセージ** ] タブに一覧表示されます。エラーの重大度によっては、処理エラーが発生したメッセージ、またはに関連するメッセージが、黄色 (警告レベル) または赤色 (エラーレベル) で強調表示されます。 メッセージをダブルクリックすると、要求の処理のコンテキストに従ってメッセージ トレースが表示されます。  
  
> [!NOTE]
> メッセージにヘッダーがない場合は、`<header/>` タグがログに記録されません。  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>クライアント、中継、およびサービスによって記録されたメッセージの表示  

 環境には、クライアント、クライアントからメッセージが送信される中継、中継からさらにメッセージが転送されるサービスが含まれることがあります。 3つのすべての場所でメッセージログが有効になっていて、3つのメッセージログがすべて [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) で同時に表示されている場合、メッセージログの交換は誤って表示されます。 これは、メッセージ ヘッダーの `CorrelationId` と `ActivityId` が、すべての送受信ペアで一意にならなくなるためです。  
  
 この問題を解決するには、次のいずれかの方法に従います。  
  
- [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)の3つのメッセージログのうち、常に2つだけを表示します。  
  
- [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)の3つのログをすべて同時に表示する必要がある場合は、新しいインスタンスを作成してリレーサービスを変更でき <xref:System.ServiceModel.Channels.Message> ます。 このインスタンスは、受信メッセージの本文のコピーであり、また、`ActivityId` ヘッダーおよび `Action` ヘッダーを除くすべてのヘッダーのコピーであることが必要です。 これを実行する方法を次のコード例に示します。  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>メッセージ ログ内容が不正確になる例外的なケース  

 次の条件では、ログ記録されたメッセージがネットワーク上にあるオクテット ストリームの正確な表現とはならない場合があります。  
  
- BasicHttpBinding の場合、エンベロープ ヘッダーは /addressing/none 名前空間の受信メッセージについてログ記録されます。  
  
- 空白は一致しない可能性があります。  
  
- 受信メッセージの場合、空の要素が異なる表現になる場合があります。 たとえば、 \<tag> \</tag> の代わりに\<tag/>  
  
- 既知の PII ログ記録が、既定または enableLoggingKnownPii="true" という明示的な設定で、無効になっている場合。  
  
- UTF-8 へ変換するためのエンコードが有効な場合。  
  
## <a name="see-also"></a>関連項目

- [サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [メッセージ ログ](message-logging.md)
