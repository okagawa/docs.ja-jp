---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 16fb6b3b63c848ea6c09cc18b0fcc488670f0926
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397476"
---
# <a name="-netcf"></a>-netcf

.NET Compact Framework を対象とするようにコンパイラを設定します。

## <a name="syntax"></a>構文

```console
-netcf
```

## <a name="remarks"></a>Remarks

`-netcf` オプションを指定すると、Visual Basic コンパイラの対象は、完全な .NET Framework ではなく .NET Compact Framework となります。 完全な .NET Framework にのみ存在する言語機能は無効になります。

`-netcf` オプションは、[-sdkpath](sdkpath.md) と共に使用するように設計されています。 `-netcf` によって無効にされた言語機能は、`-sdkpath` の対象となるファイルには存在しないものと同じ言語機能です。

> [!NOTE]
> `-netcf` オプションは、Visual Studio 開発環境内からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。 `-netcf` オプションは、Visual Basic デバイス プロジェクトが読み込まれるときに設定されます。

`-netcf` オプションでは、次の言語機能を変更します。

- プログラムの実行を終了する、[End \<keyword> ステートメント](../../language-reference/statements/end-keyword-statement.md) キーワードは無効になります。 次のプログラムは `-netcf` なしでコンパイルされ、実行されますが、`-netcf` を指定するとコンパイル時に失敗します。

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- すべての形式の遅延バインディングが無効になります。 コンパイル時のエラーは、認識された遅延バインディングのシナリオが検出された場合に生成されます。 次のプログラムは `-netcf` なしでコンパイルされ、実行されますが、`-netcf` を指定するとコンパイル時に失敗します。

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [Auto](../../language-reference/modifiers/auto.md)、[Ansi](../../language-reference/modifiers/ansi.md)、および [Unicode](../../language-reference/modifiers/unicode.md) 修飾子は無効になります。 [Declare ステートメント](../../language-reference/statements/declare-statement.md)の構文も `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` に変更されます。 次のコードは、コンパイル時の `-netcf` の効果を示しています。

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Visual Basic から削除された Visual Basic 6.0 キーワードを使用すると、`-netcf` の使用時に別のエラーが生成されます。 これは、次のキーワードのエラー メッセージに影響します。

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a>例

次のコードでは、C ドライブ上の .NET Compact Framework の既定のインストール ディレクトリにある mscorlib.dll と Microsoft.VisualBasic.dll のバージョンを使用して、.NET Compact Framework で `Myfile.vb` をコンパイルします。 通常は、最新バージョンの .NET Compact Framework を使用します。

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
- [-sdkpath](sdkpath.md)
