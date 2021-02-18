---
description: '詳細情報: -refonly (Visual Basic)'
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 283aa75fceead38c62c4cf10c1ffe08151aeac9c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474136"
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

**-refonly** オプションは、コンパイルのプライマリ出力を、実装アセンブリではなく参照アセンブリとする必要があることを示します。 `-refonly` パラメーターは、参照アセンブリを実行できない場合に、PDB の出力を暗黙的に無効にします。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>構文

```console
-refonly
```

## <a name="remarks"></a>Remarks

Visual Basic では、バージョン 15.3 以降の `-refonly` スイッチがサポートされています。

参照アセンブリは、ライブラリのパブリック API サーフェイスを表すために必要最小限のメタデータのみを含む特殊なアセンブリです。 これには、ビルド ツールでアセンブリを参照するときに重要なすべてのメンバーの宣言が含まれます。ただし、すべてのメンバーの実装と、その API コントラクトに影響を与えないプライベート メンバーの宣言は除外されます。 詳細については、.NET のガイドの「[参照アセンブリ](../../../standard/assembly/reference-assemblies.md)」を参照してください。

`-refonly` オプションと [`-refout`](refout-compiler-option.md) オプションは同時に指定できません。

## <a name="see-also"></a>関連項目

- [/refout](refout-compiler-option.md)
- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
