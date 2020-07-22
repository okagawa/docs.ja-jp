---
title: Option Infer ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: 977e492c1c8ec5040c22169d91268c9c2241f6c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404357"
---
# <a name="option-infer-statement"></a>Option Infer ステートメント

変数の宣言でローカル型推論を使用できるようにします。

## <a name="syntax"></a>構文

```vb
Option Infer { On | Off }
```

## <a name="parts"></a>指定項目

|用語|定義|
|---|---|
|`On`|任意。 ローカル型推論を有効にします。|
|`Off`|任意。 ローカル型推論を無効にします。|

## <a name="remarks"></a>Remarks

ファイルに `Option Infer` を設定するには、ファイルの先頭に他のソース コードよりも前に `Option Infer On` または `Option Infer Off` を入力します。 ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。

`Option Infer` を `On` に設定すると、データ型を明示的に指定せずにローカル変数を宣言できます。 コンパイラは、初期化式の型から変数のデータ型を推測します。

次の図では、`Option Infer` がオンになっています。 宣言 `Dim someVar = 2` 内の変数は、型の推定によって整数として宣言されています。

次のスクリーンショットは、Option Infer がオンの場合の IntelliSense を示しています。

![Option Infer がオンの場合の IntelliSense ビューを示すスクリーンショット。](./media/option-infer-statement/option-infer-as-integer-on.png)

次の図では、`Option Infer` がオフになっています。 宣言 `Dim someVar = 2` 内の変数は、型の推定によって `Object` として宣言されています。 この例では、[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) で、**Option Strict** 設定が**オフ** に設定されています。

次のスクリーンショットは、Option Infer がオフの場合の IntelliSense を示しています。

![Option Infer がオフの場合の IntelliSense ビューを示すスクリーンショット。](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> 変数を `Object` として宣言すると、プログラムの実行中にランタイム型が変更される場合があります。 Visual Basic では、*ボックス化*と*ボックス化解除*という操作を実行して `Object` と値型との間で変換を行いますが、このために実行速度が低下します。 ボックス化とボックス化解除の詳細については、[Visual Basic 言語の仕様](~/_vblang/spec/conversions.md#value-type-conversions)に関するページを参照してください。

型の推定は、プロシージャ レベルで適用され、クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側には適用されません。

詳細については、「[ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)」を参照してください。

## <a name="when-an-option-infer-statement-is-not-present"></a>Option Infer ステートメントが指定されていない場合

ソース コードに `Option Infer` ステートメントが含まれていない場合は、[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) の **Option Infer** 設定が使用されます。 コマンドライン コンパイラを使用している場合は、[-optioninfer](../../reference/command-line-compiler/optioninfer.md) コンパイラ オプションを使用します。

#### <a name="to-set-option-infer-in-the-ide"></a>IDE の Option Infer を設定するには

1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

2. **[コンパイル]** タブをクリックします。

3. **[Option infer]** ボックスに値を設定します。

新しいプロジェクトを作成すると、 **[コンパイル]** タブの **[Option Infer]** 設定が **[VISUAL BASIC の既定値]** ダイアログ ボックスの **[Option Infer]** 設定に設定されます。 **[VISUAL BASIC の既定値]** ダイアログ ボックスにアクセスするには、 **[ツール]** メニューで **[オプション]** をクリックします。 **[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。 **[VISUAL BASIC の既定値]** の初期の既定値は `On` です。

#### <a name="to-set-option-infer-on-the-command-line"></a>コマンド ラインで Option Infer を設定するには

**vbc** コマンドに [-optioninfer](../../reference/command-line-compiler/optioninfer.md) コンパイラ オプションを含めます。

## <a name="default-data-types-and-values"></a>既定のデータ型と値

次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。

|データ型が指定されているか|初期化子が指定されているか|例|結果|
|---|---|---|---|
|いいえ|いいえ|`Dim qty`|`Option Strict` がオフ (既定値) の場合、変数は `Nothing` に設定されます。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|
|いいえ|はい|`Dim qty = 5`|`Option Infer` がオン (既定値) の場合、変数は初期化子のデータ型になります。 「[ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)」を参照してください。<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|
|はい|いいえ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。 詳細については、「[Dim ステートメント](dim-statement.md)」を参照してください。|
|はい|はい|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|

## <a name="example"></a>例

次の例では、`Option Infer` ステートメントがローカル型推論をどのように有効にするかを示します。

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a>例

次の例では、変数が `Object` として識別されたときに、ランタイム型が異なる場合があることを示します。

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a>関連項目

- [Dim ステートメント](dim-statement.md)
- [ローカル型の推論](../../programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare ステートメント](option-compare-statement.md)
- [Option Explicit ステートメント](option-explicit-statement.md)
- [Option Strict ステートメント](option-strict-statement.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [-optioninfer](../../reference/command-line-compiler/optioninfer.md)
- [ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
