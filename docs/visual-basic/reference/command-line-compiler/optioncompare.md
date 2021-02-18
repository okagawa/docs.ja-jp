---
description: '詳細情報: -optioncompare'
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: 9be4867c75cc16a8f699cf492dc41e9d08b96495
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475930"
---
# <a name="-optioncompare"></a>-optioncompare

文字列比較の方法を指定します。

## <a name="syntax"></a>構文

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a>Remarks

次の 2 つの形式のいずれかで `-optioncompare` を指定できます。バイナリ文字列比較を使用する `-optioncompare:binary` と、テキスト文字列比較を使用する `-optioncompare:text` です。 コンパイラでは既定で `-optioncompare:binary` が使用されます。

Microsoft Windows では、現在のコード ページによってバイナリ並べ替え順序が決定されます。 一般的なバイナリ並べ替え順序は次のとおりです。

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

テキストベースの文字列比較は、システムのロケールによって決まる、大文字と小文字を区別しないテキストの並べ替え順序に基づきます。 一般的なテキストの並べ替え順序は次のとおりです。

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Visual Studio IDE で -optioncompare を設定するには

1. **ソリューション エクスプローラー** でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

2. **[コンパイル]** タブをクリックします。

3. **[Option Compare]** ボックスで値を変更します。

### <a name="to-set--optioncompare-programmatically"></a>-optioncompare をプログラムで設定するには

「[Option Compare ステートメント](../../language-reference/statements/option-compare-statement.md)」を参照してください。

## <a name="example"></a>例

次のコードでは `ProjFile.vb` がコンパイルされ、バイナリ文字列比較が使用されます。

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
- [Option Compare ステートメント](../../language-reference/statements/option-compare-statement.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
