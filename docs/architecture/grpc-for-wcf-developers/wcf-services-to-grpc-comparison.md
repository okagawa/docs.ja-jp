---
title: Wcf 開発者向けの WCF と gRPC-gRPC の比較
description: 分散アプリケーションを構築するための WCF および gRPC フレームワークの比較。
ms.date: 12/15/2020
ms.openlocfilehash: 7dd41c3d6f248bb1ef5eacb323b1443c7bc575a7
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938495"
---
# <a name="comparing-wcf-to-grpc"></a>WCF と gRPC の比較

前の章では、Protobuf と gRPC がメッセージを処理する方法について詳しく説明しました。 Windows Communication Foundation (WCF) から gRPC への詳細な変換を行う前に、gRPC で WCF で利用可能な機能がどのように処理されるか、および同等の gRPC がない場合に使用できる回避策について理解しておく必要があります。 特に、この章では次の項目について説明します。

- 操作とメソッド
- バインドとトランスポート
- RPC の種類
- メタデータ
- エラー処理
- \*プロトコル

## <a name="grpc-example"></a>gRPC の例

Visual Studio 2019 またはコマンドラインから新しい ASP.NET Core 5.0 gRPC プロジェクトを作成すると、"Hello World" に相当する gRPC が生成されます。 `greeter.proto`サービスとそのメッセージ、および `GreeterService.cs` サービスの実装を含むファイルを定義するファイルで構成されます。

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message that contains the user's name.
message HelloRequest {
  string name = 1;
}

// The response message that contains the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

この章では、gRPC のさまざまな概念と機能について説明するときに、このコード例を参照します。

>[!div class="step-by-step"]
>[前へ](protobuf-maps.md)
>[次へ](wcf-endpoints-grpc-methods.md)
