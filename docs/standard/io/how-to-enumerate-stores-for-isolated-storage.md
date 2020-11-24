---
title: '方法 : 分離ストレージでストアを列挙する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
ms.openlocfilehash: 9c7163dda34f254320ab7da86856d8731cd39426
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830767"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>方法 : 分離ストレージでストアを列挙する
<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> 静的メソッドを使用すると、現在のユーザー用の分離ストアをすべて列挙できます。 このメソッドは、<xref:System.IO.IsolatedStorage.IsolatedStorageScope> 値を取り、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 列挙子を返します。 ストアを列挙する場合、<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> 値を指定する <xref:System.Security.Permissions.IsolatedStorageFilePermission> のアクセス許可が必要です。 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> 値を使用して <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> メソッドを呼び出す場合、現在のユーザーに対して定義された <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトの配列が返されます。  
  
## <a name="example"></a>例  
 次のコード例は、ユーザーおよびアセンブリ別に分離されたストアを取得し、いくつかファイルを作成し、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> メソッドを使用してそれらのファイルを取得します。  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>参照

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [分離ストレージ](isolated-storage.md)
