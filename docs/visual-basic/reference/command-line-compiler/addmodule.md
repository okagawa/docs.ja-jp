---
description: '詳細情報: -addmodule'
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: ca08aa599003897e680240af21c4a0eb568e31d8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468292"
---
# <a name="-addmodule"></a>-addmodule

指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引数  

 `fileList`  
 必須です。 メタデータは含まれるが、アセンブリ マニフェストは含まれないファイルのコンマ区切りのリスト。 ファイル名に空白が含まれる場合は、名前を二重引用符 ("") で囲みます。  
  
## <a name="remarks"></a>Remarks  

 `fileList` パラメーターで指定するファイルは、`-target:module` オプションを使用して作成するか、`-target:module` と同等の別のコンパイラを使用して作成する必要があります。  
  
 `-addmodule` で追加したモジュールはすべて、実行時に出力ファイルと同じディレクトリに置かれている必要があります。 つまり、コンパイル時には任意のディレクトリからモジュールを指定できますが、実行時にはアプリケーション ディレクトリにこのモジュールが置かれている必要があります。 そうでない場合、<xref:System.TypeLoadException> エラーが発生します。  
  
 `-addmodule` で `-target:module` 以外の [-target (Visual Basic)](target.md) オプションを (暗黙的または明示的に) 指定すると、`-addmodule` に渡すファイルはプロジェクトのアセンブリの一部になります。 `-addmodule` で追加された 1 つ以上のファイルを含む出力ファイルを実行するには、アセンブリが必要です。  
  
 アセンブリが含まれるファイルからメタデータをインポートするには、[-reference (Visual Basic)](reference.md) を使用します。  
  
> [!NOTE]
> `-addmodule` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。  
  
## <a name="example"></a>例  

 モジュールは、次のコード例で作成されます。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 次のコードにより、モジュールの型がインポートされます。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 `t1` を実行すると、`802` が出力されます。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [-target (Visual Basic)](target.md)
- [-reference (Visual Basic)](reference.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
