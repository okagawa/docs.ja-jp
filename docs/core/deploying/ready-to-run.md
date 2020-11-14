---
title: ReadyToRun 展開の概要
description: ReadyToRun 展開の概要と、.NET 5 および .NET Core 3.0 以降でのアプリの発行の一部としてその使用を検討する必要がある理由について説明します。
author: davidwr
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: cd8eaebd05d79b11e90e255e702a52220fffda76
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342632"
---
# <a name="readytorun-compilation"></a>ReadyToRun コンパイル

アプリケーション アセンブリを ReadyToRun (R2R) 形式としてコンパイルすることにより、.NET アプリケーションの起動時間と待機時間を向上させることができます。 R2R とは、Ahead-Of-Time (AOT) コンパイルの一種です。

R2R バイナリでは、アプリケーションの読み込み時に Just-In-Time (JIT) コンパイラで行う必要がある作業量を減らすことにより、起動時のパフォーマンスが向上します。 バイナリには、JIT で生成されるものと似たネイティブ コードが含まれます。 ただし、R2R バイナリは、中間言語 (IL) コード (一部のシナリオでまだ必要です) と同じコードのネイティブ バージョンの両方が含まれるため、大きくなります。 R2R は、Linux x64 や Windows x64 などの特定のランタイム環境 (RID) を対象とするアプリを発行するときにのみ使用できます。

プロジェクトを ReadyToRun としてコンパイルするには、PublishReadyToRun プロパティを true に設定して、アプリケーションを発行する必要があります。

アプリを ReadyToRun として発行するには、次の 2 つの方法があります。

01. PublishReadyToRun フラグを dotnet publish コマンドに対して直接指定します。 詳細については、「[dotnet publish](../tools/dotnet-publish.md)」を参照してください。

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. プロジェクトでプロパティを指定します

    - `<PublishReadyToRun>` の設定をプロジェクトに追加します。

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - 特別なパラメーターを指定せずにアプリケーションを発行します。

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a>ReadyToRun 機能を使用した場合の影響

Ahead Of Time コンパイルには、アプリケーションのパフォーマンスに対して複雑な影響があり、予測が困難な場合があります。 一般に、アセンブリのサイズは 2 から 3 倍の大きさになります。 このようにファイルの物理サイズが大きくなると、ディスクからのアセンブリの読み込みのパフォーマンスが低下し、プロセスの作業セットが大きくなる可能性があります。 ただし、代わりに、実行時にコンパイルされるメソッドの数は一般に大幅に減少します。 その結果、大量のコードを使用するほとんどのアプリケーションでは、ReadyToRun を有効にすることにより、パフォーマンスに関して大きなメリットがあります。 ReadyToRun によって .NET ランタイム ライブラリが既にプリコンパイルされているため、コードの量が少いアプリケーションでは、ReadyToRun を有効にしてもそれほど向上しない可能性があります。

ここで説明する起動に関する向上は、アプリケーションの起動時だけでなく、アプリケーションで何かのコードを初めて使用するときにも当てはまります。 たとえば、ReadyToRun を使用すると、ASP.NET アプリケーションで Web API を初めて使用するときの応答待機時間を短縮できます。

### <a name="interaction-with-tiered-compilation"></a>階層型コンパイルとの相互作用

Ahead Of Time で生成されるものは、JIT によって生成されるコードほど高度に最適化されていません。 この問題に対処するため、階層型コンパイルでは、一般的に使用される ReadyToRun メソッドが、JIT で生成されるメソッドに置き換えられます。

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a>プリコンパイルされるアセンブリのセットが選択される方法

SDK により、アプリケーションと共に配布されるアセンブリがプリコンパイルされます。 自己完結型アプリケーションの場合、このアセンブリのセットにはフレームワークが含まれます。 C++/CLI バイナリは、ReadyToRun コンパイルの対象にはなりません。

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a>プリコンパイルされるメソッドのセットが選択される方法

コンパイラでは、可能な限り多くのメソッドのプリコンパイルが試みられます。 ただし、さまざまな理由で、ReadyToRun 機能を使用しても JIT が実行されなくなることは期待できません。

その理由には、次のようなものがあります。

- 別のアセンブリで定義されているジェネリック型の使用
- ネイティブ コードとの相互運用
- ターゲット コンピューターで使用しても安全であることをコンパイラで証明できないハードウェア組み込みの使用
- 特定の異常な IL パターン
- リフレクションによる動的メソッドの作成、または LINQ

## <a name="cross-platformarchitecture-restrictions"></a>クロス プラットフォーム/アーキテクチャの制限

一部の SDK プラットフォームでは、ReadyToRun コンパイラにより他のターゲットプラットフォームに対するクロスコンパイルを行うことができます。 サポートされているコンパイル ターゲットについては、次の表で説明します。

| SDK プラットフォーム | サポート対象のターゲット プラットフォーム |
| ------------ | --------------------------- |
| Windows X64  | Windows X86、Windows X64、Windows ARM32、Windows ARM64 |
| Windows X86  | Windows X86、Windows ARM32 |
| Linux X64    | Linux X86、Linux X64、Linux ARM32、Linux ARM64 |
| Linux ARM32  | Linux ARM32 |
| Linux ARM64  | Linux ARM64 |
| macOS X64    | macOS X64 |
