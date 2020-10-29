---
ms.openlocfilehash: ee67b32b093ebd42f8ac685b34b12f2f6833be86
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332928"
---
### <a name="threadabort-is-obsolete"></a>Thread.Abort は古い形式

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> API は非推奨になっています。 .NET 5.0 以降のバージョンを対象とするプロジェクトでは、これらのメソッドが呼び出されると、コンパイル時の警告 `SYSLIB0006` が発生します。

#### <a name="change-description"></a>変更内容

以前は、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出したときにコンパイル時の警告は生成されませんでしたが、このメソッドによって実行時に <xref:System.PlatformNotSupportedException> がスローされていました。

.NET 5.0 以降、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> は警告として古い形式を示すマークが付けられるようになりました。 このメソッドを呼び出すと、コンパイラの警告 `SYSLIB0006` が生成されます。 メソッドの実装は変更されず、引き続き <xref:System.PlatformNotSupportedException> がスローされます。

#### <a name="reason-for-change"></a>変更理由

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> により、.NET Framework を除くすべての .NET 実装で常に <xref:System.PlatformNotSupportedException> がスローされることを考慮して、呼び出される場所に注意を促すためにメソッドに <xref:System.ObsoleteAttribute> が追加されました。

#### <a name="version-introduced"></a>導入されたバージョン

5.0 RC 1

#### <a name="recommended-action"></a>推奨アクション

- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出す代わりに、<xref:System.Threading.CancellationToken> を使用して作業単位の処理を中止します。 次の例は、<xref:System.Threading.CancellationToken>の使用方法を示しています。

  ```csharp
  void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
  {
      if (QueryIsMoreWorkPending())
      {
          // If the CancellationToken is marked as "needs to cancel",
          // this will throw the appropriate exception.
          cancellationToken.ThrowIfCancellationRequested();

          WorkItem work = DequeueWorkItem();
          ProcessWorkItem(work);
      }
  }
  ```

  詳細については、「[マネージド スレッドのキャンセル](../../../../docs/standard/threading/cancellation-in-managed-threads.md)」を参照してください。

- コンパイル時の警告が表示されないようにするには、警告コード `SYSLIB0006` を抑制します。 警告コードは <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> に固有であり、これを抑制しても、コード内の他の非推奨警告は抑制されません。 しかし、警告を抑制するのではなく、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> の呼び出しを削除することをお勧めします。

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  また、プロジェクト ファイルで警告を抑制することもできます。

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a>カテゴリ

- Core .NET ライブラリ

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
