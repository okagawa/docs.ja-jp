---
description: 詳細については、バイトストリーム Encoder を使用したバイナリオブジェクトのエンコードに関するページをご覧ください。
title: バイトストリーム エンコーダーを使用したバイナリ オブジェクトのエンコーディング
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 4ef3d3cd378abacd14dd502530a8090f3982e4ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704902"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>バイトストリーム エンコーダーを使用したバイナリ オブジェクトのエンコーディング

Windows Communication Foundation (WCF) での生のバイナリデータの送受信は、を使用して構成し <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> ます。  
  
## <a name="byte-stream-message-encoder-architecture"></a>バイト ストリーム メッセージ エンコーダーのアーキテクチャ  

 WCF によって使用されるバイナリメッセージエンコーダーには、メッセージ内の基になるバイナリデータを処理、検証、または識別する機能がありません。 データ パッケージは、XML にエンコード、送受信、およびデコードされます。 エンコーダーは、トランスポートに渡された後に、メッセージがメッセージ キューに送られる前にデータを処理します。 機能的には、バイナリ エンコーダーが、送信用にメッセージ データを `<binary>` 要素にラップし、そのメッセージが受信された後にこの要素を削除します。  
  
## <a name="using-the-byte-stream-message-encoder"></a>バイト ストリーム メッセージ エンコーダーの使用  

 次の例は、バイト ストリーム メッセージ エンコーダーを実装するサービス コントラクトを示しています。  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 次の例は、呼び出されたサービスを示しています。  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 ルーターなどのメッセージ インフラストラクチャを実装するサービスを使用する場合、そのメッセージは、次の例に示すように、メッセージの検査、検証、およびメッセージとの対話操作のいずれも行うことなく処理されます。  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>シナリオ  

 バイト ストリーム エンコーダーは、次のシナリオに役立ちます。  
  
- WCF を使用してコンピューター間で JPEG イメージを転送する。 このシナリオでは、イメージは外部ソースから転送によって到着し、送信されたデータはイメージを構成する生バイトになります。 サービスはバイナリ データを受信してイメージを表示します。  
  
- メッセージ キューからの情報の読み取りと処理。 メッセージはメッセージ キュー マネージャーから読み取られ、処理対象のメッセージ キュー チャネルに渡されます。 メッセージキューチャネルは、WCF チャネルスタック内のキューマネージャーとして機能します。  
  
 メッセージをメッセージ キュー チャネルを介して送信する場合、送信者はキュー マネージャーから受信したバイトを制御できません。 受信プロセスで生バイトを読み取ることができない場合、メッセージは不適切な書式として受信され処理されません。受信プロセスは受信したバイトを利用可能な形式に変換する機能があると見なされます。
