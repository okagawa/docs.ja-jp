---
title: SYSLIB0010 警告
description: コンパイル時の警告 SYSLIB0010 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 289fb3f766a6e1d37bea8faec1896d20442f43f9
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596302"
---
# <a name="syslib0010-unsupported-remoting-apis"></a>SYSLIB0010:サポートされていないリモート処理 API

[.NET リモート処理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))は従来のテクノロジであり、インフラストラクチャは .NET Framework にのみ存在します。 .NET 5.0 以降、次のリモート処理関連の API は古いものとしてマークされています。 これらをコードで使用すると、コンパイル時に警告 `SYSLIB0010` が生成されます。

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workarounds"></a>回避策

他のアプリケーションの、または複数のコンピューターのオブジェクトと通信する場合は、WCF または HTTP ベースの REST サービスの使用を検討してください。 詳細については、[.NET Core で使用できない .NET Framework テクノロジ](../../porting/net-framework-tech-unavailable.md)に関するページを参照してください。

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>関連項目

- [.NET リモート処理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))
