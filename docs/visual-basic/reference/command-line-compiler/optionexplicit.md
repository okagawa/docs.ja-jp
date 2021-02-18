---
description: '詳細情報: -optionexplicit'
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 4d1ab14bbf9de176de17fb5077f4bb919f5472b4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433563"
---
# <a name="-optionexplicit"></a>-optionexplicit

変数が使用される前に宣言されていない場合、コンパイラによってエラーが報告されます。  
  
## <a name="syntax"></a>構文  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引数  

 `+` &#124; `-`  
 任意。 変数の明示的な宣言を要求するには、`-optionexplicit+` を指定します。 `-optionexplicit+` オプションは既定値であり、`-optionexplicit` と同じです。 `-optionexplicit-` オプションを使用すると、変数の暗黙的な宣言を行うことができます。  
  
## <a name="remarks"></a>Remarks  

 ソース コード ファイルに [Option Explicit ステートメント](../../language-reference/statements/option-explicit-statement.md)が含まれている場合、そのステートメントによって `-optionexplicit` コマンドライン コンパイラ設定がオーバーライドされます。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Visual Studio IDE で -optionexplicit を設定するには  
  
1. **ソリューション エクスプローラー** でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。
  
2. **[コンパイル]** タブをクリックします。  
  
3. **[Option Explicit]** ボックスで値を変更します。  
  
## <a name="example"></a>例  

 `-optionexplicit-` が使用されている場合、次のコードがコンパイルされます。  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [-optioncompare](optioncompare.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
- [Option Explicit ステートメント](../../language-reference/statements/option-explicit-statement.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
