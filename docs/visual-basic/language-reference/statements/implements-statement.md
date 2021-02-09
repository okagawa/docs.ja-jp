---
description: '詳細情報: Implements ステートメント'
title: Implements ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: aa53d1f3b4ba9d9111f5ffb09198a11511f8d9e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768988"
---
# <a name="implements-statement"></a>Implements ステートメント

それが存在するクラスまたは構造体の定義に、実装する必要のある 1 つ以上のインターフェイス、つまりインターフェイス メンバーを指定します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>指定項目  

 `interfacename`  
 必須です。 クラスまたは構造体に、対応するメンバーによって実装されるプロパティ、プロシージャ、およびイベントを持つインターフェイス。  
  
 `interfacemember`  
 必須です。 実装されるインターフェイスのメンバー。  
  
## <a name="remarks"></a>Remarks  

 インターフェイスは、インターフェイスによってカプセル化されるメンバー (プロパティ、プロシージャ、およびイベント) を表すプロトタイプのコレクションです。 インターフェイスには、メンバーの宣言のみが含まれます。クラスと構造体で、これらのメンバーを実装します。 詳細については、「[インターフェイス](../../programming-guide/language-features/interfaces/index.md)」を参照してください。  
  
 `Implements` ステートメントは、`Class` または `Structure` ステートメントの直後に記述する必要があります。  
  
 インターフェイスを実装する場合は、インターフェイスで宣言されたすべてのメンバーを実装する必要があります。 メンバーを省略すると、構文エラーと見なされます。 個々のメンバーを実装するには、クラスまたは構造体でメンバーを宣言するときに、[Implements](implements-clause.md) キーワード (`Implements` ステートメントとは別) を指定します。 詳細については、「[インターフェイス](../../programming-guide/language-features/interfaces/index.md)」を参照してください。  
  
 クラスでは、プロパティとプロシージャの [Private](../modifiers/private.md) 実装を使用できますが、インターフェイスの型として宣言された変数に、実装するクラスのインスタンスをキャストすることによってのみ、これらのメンバーにアクセスできます。  
  
## <a name="example"></a>例  

 次の例は、`Implements` ステートメントを使用して、インターフェイスのメンバーを実装する方法を示しています。 これは、イベント、プロパティ、およびプロシージャを含む `ICustomerInfo` という名前のインターフェイスを定義しています。 クラス `customerInfo` では、インターフェイスで定義されているすべてのメンバーを実装します。  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 クラス `customerInfo` では、別のソース コード行で `Implements` ステートメントを使用して、クラスで `ICustomerInfo` インターフェイスのすべてのメンバーを実装していることを示していることに注意してください。 次に、クラスの各メンバーで、そのメンバー宣言の一部として `Implements` キーワードを使用して、そのインターフェイス　メンバーを実装していることを示しています。  
  
## <a name="example"></a>例  

 次の 2 つのプロシージャでは、前の例で実装したインターフェイスを使用する方法を示しています。 実装をテストするには、これらのプロシージャをプロジェクトに追加し、`testImplements` プロシージャを呼び出します。  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>関連項目

- [Implements](implements-clause.md)
- [Interface ステートメント](interface-statement.md)
- [インターフェイス](../../programming-guide/language-features/interfaces/index.md)
