---
title: '方法: 分離ストレージでファイルおよびディレクトリを作成する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: b9ae108d9416bb834fc230fde1e62b929c21eb20
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990168"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>方法: 分離ストレージでファイルおよびディレクトリを作成する

分離ストアを取得したら、データを格納するためのディレクトリとファイルを作成することができます。 ストア内では、ファイル名とディレクトリ名は仮想ファイル システムのルートに対して指定されます。  
  
 ディレクトリを作成するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> インスタンス メソッドを使用します。 存在しないディレクトリのサブディレクトリを指定した場合、両方のディレクトリが作成されます。 既に存在するディレクトリを指定した場合、メソッドはディレクトリを作成せずに制御を返し、例外はスローされません。 ただし、無効な文字を含むディレクトリ名を指定した場合、<xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外がスローされます。  
  
 ファイルを作成するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> メソッドを使用します。  
  
 Windows オペレーティング システムでは、分離ストレージ ファイルおよびディレクトリの名前の大文字と小文字は区別されません。 つまり、`ThisFile.txt` という名前のファイルを作成してから `THISFILE.TXT` という名前の別のファイルを作成した場合、作成されるのは 1 つのファイルのみです。 ファイル名では、表示目的で元の大文字と小文字の区別が保持されます。  

 存在しないディレクトリがパスに含まれている場合、分離ストレージ ファイルを作成すると、<xref:System.IO.IsolatedStorage.IsolatedStorageException> がスローされます。
  
## <a name="example"></a>例  
 分離ストア内にファイルおよびディレクトリを作成する方法を次のコード例で示します。  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [分離ストレージ](isolated-storage.md)
