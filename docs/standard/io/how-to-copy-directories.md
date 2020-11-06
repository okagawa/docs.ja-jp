---
title: '方法: ディレクトリをコピーする'
description: 別の場所にディレクトリの内容を同期的にコピーする I/O クラスを使用してディレクトリをコピーする方法を参照します。
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET], copying directories
- subdirectory copying
- copying directories
- directories [.NET], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 476473d5c25ce29d070abbeef7fa29a7cb9621e1
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187984"
---
# <a name="how-to-copy-directories"></a>方法: ディレクトリをコピーする

この記事では、I/O クラスを使用して、別の場所にディレクトリの内容を同期的にコピーする方法について説明します。

ファイルを非同期的にコピーする例については、「[非同期ファイル I/O](asynchronous-file-i-o.md)」を参照してください。

この例では、`DirectoryCopy` メソッドの `copySubDirs` を `true` に設定することでサブディレクトリをコピーします。 `DirectoryCopy` メソッドは各サブディレクトリでそれ自体を呼び出すことで、コピーするサブディレクトリがなくなるまでサブディレクトリを再帰的にコピーします。  
  
## <a name="example"></a>例  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>関連項目

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [ファイルおよびストリーム入出力](index.md)
- [共通 I/O タスク](common-i-o-tasks.md)
- [非同期ファイル I/O](asynchronous-file-i-o.md)
