---
description: '詳細情報: -debug (Visual Basic)'
title: -debug
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 44f1c1d233ff8ed38b6e96ef316bc118c269316b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467031"
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)

コンパイラによってデバッグ情報が生成され、出力ファイルに配置されます。

## <a name="syntax"></a>構文

```console
-debug[+ | -]
```

or

```console
-debug:[full | pdbonly]
```

## <a name="arguments"></a>引数

|用語|定義|
|---|---|
|`+` &#124; `-`|任意。 `+` または `-debug` を指定すると、コンパイラによってデバッグ情報が生成され、.pdb ファイルに配置されます。 `-` を指定することは、`-debug` を指定しない場合と同じ効果があります。|
|`full` &#124; `pdbonly`|任意。 コンパイラによって生成されるデバッグ情報の種類を指定します。 `-debug:pdbonly` を指定しない場合、既定値は `full` になります。これにより、実行中のプログラムにデバッガーをアタッチできます。 `pdbonly` 引数を指定すると、プログラムがデバッガーで開始されたときに、ソースコードのデバッグが可能になりますが、実行中のプログラムがデバッガーにアタッチされているときにのみアセンブリ言語コードが表示されます。|

## <a name="remarks"></a>Remarks

このオプションを使用してデバッグ ビルドを作成します。 `-debug`、`-debug+`、または `-debug:full` を指定しない場合は、プログラムの出力ファイルをデバッグできません。

既定では、デバッグ情報は生成されません (`-debug-`)。 デバッグ情報を生成するには、`-debug` または `-debug+` を指定します。

アプリケーションのデバッグ パフォーマンスを構成する方法については、「[イメージのデバッグの簡略化](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)」を参照してください。

|Visual Studio 統合開発環境で -debug を設定するには|
|---|
|1.**ソリューション エクスプローラー** でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2. **[コンパイル]** タブをクリックします。<br />3. **[詳細コンパイル オプション]** をクリックします。<br />4. **[デバッグ情報を作成]** ボックスで値を変更します。|

## <a name="example"></a>例

次の例では、デバッグ情報を出力ファイル `App.exe` に配置します。

```console
vbc -debug -out:app.exe test.vb
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [-bugreport](bugreport.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
