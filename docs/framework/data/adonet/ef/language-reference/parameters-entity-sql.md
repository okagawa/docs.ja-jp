---
description: '詳細情報: パラメーター (Entity SQL)'
title: パラメーター (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 77b1e6ee95b5d367fec8d99345bbb416c2b9787d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724532"
---
# <a name="parameters-entity-sql"></a>パラメーター (Entity SQL)

パラメーターは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の外部で定義される変数です。通常は、ホスト言語で使用されるバインド API を通じて定義されます。 それぞれのパラメーターには、名前と型があります。 パラメーター名は、クエリ式の中で、先頭に @ 記号を付けることによって定義します。 これにより、クエリ内で定義されている他の名前 (プロパティ名など) と明確に区別されます。  
  
 パラメーターをバインドするための API は、ホスト言語によって提供されます。  
  
## <a name="example"></a>例  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [Entity SQL の概要](entity-sql-overview.md)
