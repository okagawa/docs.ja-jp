---
title: 例外の作成とスロー - C# プログラミング ガイド
description: 例外の作成とスローについて説明します。 例外は、プログラムの実行中にエラーが発生したことを示すために使われます。
ms.date: 12/09/2020
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: a6998c5b274736b290460808ad4c7cb22be7ebf6
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110209"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>例外の作成とスロー (C# プログラミング ガイド)

例外は、プログラムの実行中にエラーが発生したことを示すために使われます。 エラーを説明する例外オブジェクトが作成された後、[throw](../../language-reference/keywords/throw.md) キーワードで "*スロー*" されます。 そのとき、ランタイムは最も互換性のある例外ハンドラーを検索します。

プログラマは、以下の条件が 1 つでも該当するときは、例外をスローする必要があります。

- メソッドは、定義されている機能を完了できません。 たとえば、メソッドへのパラメーターに無効な値が設定されている場合などです。
  :::code language="csharp" source="snippets/exceptions/Program.cs" ID="CantComplete":::
- オブジェクトの状態に基づくと、オブジェクトに対して行われた呼び出しが不適切です。 たとえば、読み取り専用ファイルに書き込もうとしたような場合です。 オブジェクトの状態により操作が許可されない場合は、<xref:System.InvalidOperationException> のインスタンスまたはこのクラスの派生に基づくオブジェクトをスローします。 次のコードは、<xref:System.InvalidOperationException> オブジェクトをスローするメソッドの例です。
  :::code language="csharp" source="snippets/exceptions/ProgramLog.cs" ID="ProgramLog":::
- メソッドへの引数が原因で例外が発生しました。 この場合は、元の例外をキャッチして、<xref:System.ArgumentException> のインスタンスを作成する必要があります。 元の例外は、<xref:System.Exception.InnerException%2A> パラメーターとして <xref:System.ArgumentException> のコンストラクターに渡す必要があります。
  :::code language="csharp" source="snippets/exceptions/Program.cs" ID="InvalidArg":::

例外には、<xref:System.Exception.StackTrace%2A> というプロパティが含まれています。 この文字列には、現在の呼び出し履歴でのメソッドの名前と、各メソッドの例外がスローされたファイル名と行番号が含まれます。 スタック トレースを開始するポイントから例外をスローする必要があるため、共通言語ランタイム (CLR) によって `throw` ステートメントのポイントから <xref:System.Exception.StackTrace%2A> オブジェクトが自動的に作成されます。

すべての例外には、<xref:System.Exception.Message%2A> というプロパティが含まれています。 例外の原因を説明するには、この文字列を設定する必要があります。 機密性の高い情報はメッセージ テキストに入れないようにする必要があります。 <xref:System.ArgumentException> には、<xref:System.Exception.Message%2A> に加え、例外がスローされる原因となる引数の名前に設定される <xref:System.ArgumentException.ParamName%2A> というプロパティが含まれています。 プロパティ セッターでは、<xref:System.ArgumentException.ParamName%2A> は `value` に設定する必要があります。

public と protected メソッドからは、意図された機能を完了できない場合、常に例外がスローされる必要があります。 スローされる例外クラスは、エラー状態に適合する使用可能な例外の中で最も具体的なものになります。 これらの例外はクラスの機能の一部として文書化する必要があり、派生クラスまたは元のクラスの更新では、旧バージョンとの互換性のために同じ動作を維持する必要があります。

## <a name="things-to-avoid-when-throwing-exceptions"></a>例外をスローするときに避ける必要があること

次の一覧は、例外をスローするときに避ける必要があることです。

- プログラムのフローを変更するために、通常の実行の一部として例外を使用しないでください。 例外はエラー状態の報告と処理のために使用します。
- スローする代わりに、戻り値またはパラメーターとして例外を返さないでください。
- 独自のソース コードからは、意図的に <xref:System.Exception?displayProperty=nameWithType>、<xref:System.SystemException?displayProperty=nameWithType>、<xref:System.NullReferenceException?displayProperty=nameWithType>、または <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> をスローしないでください。
- デバッグ モードではスローでき、リリース モードではスローできない例外は、作成しないでください。 開発フェーズ中に実行時エラーを識別するには、代わりにデバッグ アサートを使ってください。

## <a name="defining-exception-classes"></a>例外クラスの定義

プログラムでは、<xref:System> 名前空間で事前定義された例外クラスをスローするか (上記の場合を除きます)、<xref:System.Exception> から派生することで独自の例外クラスを作成することができます。 派生クラスでは、少なくとも 4 つのコンストラクターを必ず定義します。パラメータ―なしのコンストラクター、メッセージ プロパティを設定するコンストラクター、<xref:System.Exception.Message%2A> プロパティと <xref:System.Exception.InnerException%2A> プロパティの両方を設定するコンストラクター、 そして 4 番目は例外のシリアル化に使われるコンストラクターです。 新しい例外クラスは、シリアル化可能にする必要があります。 次に例を示します。

:::code language="csharp" source="snippets/exceptions/InvalidDepartmentException.cs" id="DefineExceptionClass":::

新しいプロパティによって提供されるデータが例外の解決に役立つ場合は、それを例外クラスに追加します。 派生例外クラスに新しいプロパティを追加する場合は、`ToString()` をオーバーライドして追加情報を返す必要があります。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[例外](~/_csharplang/spec/exceptions.md)と [throw ステートメント](~/_csharplang/spec/statements.md#the-throw-statement)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- [例外階層](../../../standard/exceptions/index.md)
