---
title: .NET でのテスト
description: この記事では、.NET でのテストにおけるテストの概念、用語、ツールについて簡単に説明します。
author: IEvangelist
ms.author: dapine
ms.date: 10/19/2020
ms.openlocfilehash: 137a8f4e3bc9e3be529d5034c233d283cf158b31
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824858"
---
# <a name="testing-in-net"></a>.NET でのテスト

この記事では、テストの概念と、コードの検証に使用できるさまざまな種類のテストについて説明します。 .NET アプリケーションのテストには、[.NET CLI](#net-cli) や[統合開発環境 (IDE)](#ide) など、さまざまなツールを使用できます。

## <a name="test-types"></a>テストの種類

アプリケーション コードが作成者の意図どおりに動作するように自動テストを行うのは、最良の方法です。 この記事では、単体テスト、統合テスト、およびロード テストについて説明します。

### <a name="unit-tests"></a>単体テスト

"*単体テスト*" とは、"作業単位" とも呼ばれるソフトウェアの個々のコンポーネントまたはメソッドを動かすテストです。 単体テストでは、開発者の管理下でのみ、コードをテストする必要があります。 インフラストラクチャに対する懸念はテストしません。 インフラストラクチャに対する懸念とは、データベース、ファイル システム、ネットワーク リソースなどとのやりとりです。

単体テストの作成の詳細については、[テスト ツール](#testing-tools)に関する説明を参照してください。

### <a name="integration-tests"></a>統合テスト

"*統合テスト*" とは、2 つ以上のソフトウェア コンポーネントの連携機能、つまりそれらの "統合" を動かすという点で単体テストとは異なります。 単体テストでは個々のコンポーネントに着目するのに対し、これらのテストでは、テスト対象のシステムの広範な部分を動作させます。 多くの場合、統合テストにはインフラストラクチャに対する懸念も含まれます。

### <a name="load-tests"></a>ロード テスト

"*ロード テスト*" では、アプリケーションを使用する同時ユーザー数や、やりとりに対するアプリの即時応答性など、システムが指定の負荷を処理できるかどうかを判断します。 Web アプリケーションのロード テストの詳細については、「[ASP.NET Core のロード テスト/ストレス テスト](/aspnet/core/test/load-tests)」を参照してください。

## <a name="test-considerations"></a>テストに関する留意点

テストの記述には、[ベスト プラクティス](unit-testing-best-practices.md)があります。 たとえば、[テスト駆動開発 (TDD)](https://deviq.com/test-driven-development) では、単体テストを記述してからチェック対象のコードを記述します。 TDD は、本を書く前にアウトラインを作成するのと似ています。 開発者が簡潔で読みやすく、効率的なコードを記述できるように支援します。

## <a name="testing-tools"></a>テスト ツール

.NET は、複数の言語を使用できる開発プラットフォームであり、[C#](../../csharp/index.yml)、[F#](../../fsharp/index.yml)、[Visual Basic](../../visual-basic/index.yml) 向けのさまざまな種類のテストを作成できます。 これら各言語に、いくつかのテスト フレームワークを選択できます。

### <a name="xunit"></a>xUnit

[xUnit](https://xunit.net) は、.NET 用の無料のオープン ソースのコミュニティ向け単体テスト ツールです。 xUnit.net は、NUnit v2 の最初の発明者によって記述された、.NET アプリを単体テストする最新のテクノロジです。 xUnit.net は、ReSharper、CodeRush、TestDriven.NET および [Xamarin](https://dotnet.microsoft.com/apps/xamarin) と共に動作します。 これは、[.NET Foundation](https://dotnetfoundation.org) のプロジェクトであり、その行動規範の下で動作します。

詳細については、次のリソースを参照してください。

- [C# を使用した単体テスト](unit-testing-with-dotnet-test.md)
- [F# を使用した単体テスト](unit-testing-fsharp-with-dotnet-test.md)
- [Visual Basic を使用した単体テスト](unit-testing-visual-basic-with-dotnet-test.md)

### <a name="nunit"></a>NUnit

[NUnit](https://nunit.org) は、.NET の全言語で使用できる単体テスト フレームワークです。 最初に JUnit から移植された現在の運用リリースは、さまざまな .NET プラットフォーム向けの多数の新機能とサポートで書き換えられています。 これは、[.NET Foundation](https://dotnetfoundation.org) のプロジェクトです。

詳細については、次のリソースを参照してください。

- [C# を使用した単体テスト](unit-testing-with-nunit.md)
- [F# を使用した単体テスト](unit-testing-fsharp-with-nunit.md)
- [Visual Basic を使用した単体テスト](unit-testing-visual-basic-with-nunit.md)

### <a name="mstest"></a>MSTest

[MSTest](https://github.com/Microsoft/testfx-docs) は、.NET の全言語で使用できる Microsoft のテスト フレームワークです。 これは拡張可能で、.NET CLI でも Visual Studio でも動作します。 詳細については、次のリソースを参照してください。

- [C# を使用した単体テスト](unit-testing-with-mstest.md)
- [F# を使用した単体テスト](unit-testing-fsharp-with-mstest.md)
- [Visual Basic を使用した単体テスト](unit-testing-visual-basic-with-mstest.md)

### <a name="net-cli"></a>.NET CLI

[.NET CLI](../tools/index.md) からソリューションの単体テストを実行するには、[dotnet test](../tools/dotnet-test.md) コマンドを使用します。 .NET CLI では、[統合開発環境 (IDE)](#ide) からユーザー インターフェイスで使用できる機能の大部分が公開されています。 .NET CLI はクロスプラットフォームであり、継続的インテグレーションおよび配信パイプラインの一部として使用できます。 .NET CLI は、一般的なタスクを自動化するスクリプト化されたプロセスで使用されます。

### <a name="ide"></a>IDE

Visual Studio、Visual Studio for Mac、Visual Studio Code のどれを使用していても、機能のテストには、グラフィカル ユーザー インターフェイスが用意されています。 IDE には CLI よりも、[Live Unit Testing](/visualstudio/test/live-unit-testing) など多くの機能があります。 詳細については、[Visual Studio でのテストの追加と除外](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)に関する説明を参照してください。

## <a name="see-also"></a>関連項目

詳細については、以下の記事を参照してください。

- [.NET での単体テストのベスト プラクティス](unit-testing-best-practices.md)
- [ASP.NET Core での統合テスト](/aspnet/core/test/integration-tests#test-app-prerequisites)
- [選択的単体テストの実行](selective-unit-tests.md)
- [単体テストにコードカバレッジを使用する](unit-testing-code-coverage.md)
