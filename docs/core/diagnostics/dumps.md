---
title: ダンプ - .NET
description: .NET でのダンプの概要。
ms.date: 10/12/2020
ms.openlocfilehash: 7a4c7bf54b3e9ea43e685eafbd00b4a373326520
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764943"
---
# <a name="dumps"></a>ダンプ

ダンプは、その作成時におけるプロセスのスナップショットを含むファイルであり、アプリケーションの状態を調べるのに役立ちます。 運用または CI 環境などにデバッガーをアタッチするのが困難な場合に、.NET アプリケーションをデバッグするためにタンプを使用できます。 ダンプを使用すると、アプリケーションを停止しなくても、問題のあるプロセスの状態をキャプチャして調べることができます。

## <a name="collect-dumps"></a>ダンプを収集する

ダンプは、アプリを実行しているプラットフォームに応じてさまざまな方法で収集できます。

> [!NOTE]
> コンテナー内のダンプを収集するには、PTRACE 機能が必要です。これは、`--cap-add=SYS_PTRACE` または `--privileged` を使用して追加できます。

> [!NOTE]
> ダンプには、実行中のプロセスの完全なメモリが含まれている可能性があるため、機密情報が含まれている場合があります。 セキュリティに関する制限事項とガイダンスを考慮して扱うようにしてください。

### <a name="collecting-dumps-on-crash"></a>クラッシュ時のダンプの収集

環境変数を使用すると、クラッシュ時にダンプを収集するようにアプリケーションを構成できます。 これは、クラッシュが発生した理由を理解するのに役立ちます。 たとえば、例外がスローされたときにダンプをキャプチャすると、クラッシュ時にアプリの状態を調べて問題を特定するのに役立ちます。

次の表には、クラッシュ時にダンプを収集するために構成できる環境変数が示されています。

|環境変数|説明|既定値|
|-------|---------|---|
|`COMPlus_DbgEnableMiniDump`|1 に設定すると、コア ダンプ生成が有効になります。|0|
|`COMPlus_DbgMiniDumpType`|収集されるダンプの種類。 詳細については、以下の表を参照してください|2 (`MiniDumpWithPrivateReadWriteMemory`)|
|`COMPlus_DbgMiniDumpName`|ダンプの書き込み先ファイルへのパス。|`/tmp/coredump.<pid>`|
|`COMPlus_CreateDumpDiagnostics`|1 に設定すると、ダンプ プロセスの診断ログが有効になります。|0|

次の表には、`COMPlus_DbgMiniDumpType` に使用できるすべてのオプションが示されています。これは値として指定できます。 たとえば、`COMPlus_DbgMiniDumpType` を 1 に設定した場合、クラッシュ時に `MiniDumpNormal` 型ダンプが収集されることを意味します。

|値|名前|説明|
|-----|----|-----------|
|1|`MiniDumpNormal`|プロセス内のすべての既存のスレッドのスタック トレースをキャプチャするために必要な情報のみを含めます。 GC ヒープ メモリと情報が制限されます。|
|2|`MiniDumpWithPrivateReadWriteMemory`|プロセス内のすべての既存のスレッドのスタック トレースをキャプチャするために必要な GC ヒープと情報が含まれます。|
|3|`MiniDumpFilterTriage`|プロセス内のすべての既存のスレッドのスタック トレースをキャプチャするために必要な情報のみを含めます。 GC ヒープ メモリと情報が制限されます。|
|4|`MiniDumpWithFullMemory`|プロセス内のすべてのアクセス可能なメモリを含めます。 生のメモリ データは最後に含まれるため、初期構造は生のメモリ情報なしで直接マップできます。 このオプションを使用すると、ファイルが非常に大きくなる可能性があります。|

### <a name="collecting-dumps-at-specific-point-in-time"></a>特定の時点でのダンプの収集

アプリがまだクラッシュしていない場合は、ダンプを収集することができます。 たとえば、デッドロックが発生していると思われるアプリケーションの状態を確認する場合、クラッシュ時にダンプを収集するように環境変数を構成しても役に立ちません。これは、アプリがまだ実行中であるためです。

独自の要求でダンプを収集するために、ダンプを収集して分析するための CLI ツールである `dotnet-dump` を使用できます。 `dotnet-dump` を使用してダンプを収集する方法について詳しくは、「[ダンプの収集と分析のユーティリティ](dotnet-dump.md)」を参照してください。

## <a name="analyze-dumps"></a>ダンプを分析する

[`dotnet-dump`](dotnet-dump.md) CLI ツールか [Visual Studio](https://docs.microsoft.com/visualstudio/debugger/using-dump-files) を使用し、ダンプを分析できます。

> [!NOTE]
> Visual Studio バージョン 16.8 以降では、.NET Core 3.1.7 以降で生成された [Linux ダンプ](https://devblogs.microsoft.com/visualstudio/linux-managed-memory-dump-debugging/)を開くことができます。  

> [!NOTE]
> ネイティブ デバッグが必要な場合、[SOS デバッガー拡張機能](sos-debugging-extension.md)を [Linux と macOS で LLDB](debug-linux-dumps.md#analyze-dumps-on-linux) と共に使用できます。 SOS は、Windows の場合、[Windbg/cdb](/windows-hardware/drivers/debugger/debugger-download-tools) でもサポートされています。ただし、Visual Studio が推奨されています。

## <a name="see-also"></a>関連項目

.NET アプリケーションでの問題を診断するのに役立つようにダンプを活用する方法について、さらに詳しく学習します。

* [Linux ダンプのデバッグ](debug-linux-dumps.md) チュートリアルでは、Linux で収集されたダンプをデバッグする方法について説明します。

* [デッドロックのデバッグ](debug-deadlock.md) チュートリアルでは、ダンプを使用して .NET アプリケーションでデッドロックをデバッグする方法について説明します。
