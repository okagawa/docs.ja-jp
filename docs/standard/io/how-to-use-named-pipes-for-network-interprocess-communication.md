---
title: '方法: ネットワークのプロセス間通信で名前付きパイプを使用する'
description: パイプ サーバーとネットワーク内の 1 つ以上のパイプ クライアントとの間でのプロセス間通信に名前付きパイプを使用する 2 つの例を参照します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communication [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
ms.openlocfilehash: a529d1d44a903df36099a59e07f4582554d230f2
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662564"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>方法: ネットワークのプロセス間通信で名前付きパイプを使用する
名前付きパイプは、パイプ サーバーと 1 つ以上のパイプ クライアントとの間でのプロセス間通信を提供します。 名前付きパイプには、ローカル コンピューター上のプロセス間通信を提供する匿名パイプと比較して、より多くの機能が用意されています。 名前付きパイプは、ネットワーク上の複数のサーバー インスタンスでの全二重通信、メッセージ ベースの通信、およびクライアント偽装をサポートしています。偽装を使用すると、プロセスを接続してリモート サーバー上で独自のアクセス許可セットを使用できます。  
  
 名前付きパイプを実装するには、<xref:System.IO.Pipes.NamedPipeServerStream> クラスと <xref:System.IO.Pipes.NamedPipeClientStream> クラスを使用します。  
  
## <a name="example"></a>例  
 <xref:System.IO.Pipes.NamedPipeServerStream> クラスを使用して、名前付きパイプを作成する例を次に示します。 この例では、サーバー プロセスは 4 つのスレッドを作成します。 各スレッドは、1 つのクライアント接続を受け入れます。 接続されたクライアント プロセスは、サーバーにファイル名を提供します。 クライアントに十分なアクセス許可がある場合は、サーバー プロセスはファイルを開き、その内容をクライアントに送り返します。  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>例  
 次の例は、<xref:System.IO.Pipes.NamedPipeClientStream> クラスを使用するクライアント プロセスを示したものです。 クライアントはサーバー プロセスに接続し、サーバーにファイル名を送信します。 この例では偽装を使用しているため、クライアント アプリケーションを実行している ID はファイルにアクセスする権限を持っている必要があります。 サーバーは、ファイルの内容をクライアントに送り返します。 その後、ファイルの内容がコンソールに表示されます。  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ここで例示したクライアント プロセスとサーバー プロセスは、同じコンピューターで実行することを意図しているため、<xref:System.IO.Pipes.NamedPipeClientStream> オブジェクトには、`"."` というサーバー名が提供されます。 クライアント プロセスとサーバー プロセスを異なるコンピューター上で実行する場合、`"."` はサーバー プロセスを実行するコンピューターのネットワーク名で置換されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [パイプ](pipe-operations.md)
- [方法: ローカルのプロセス間通信で匿名パイプを使用する](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
