---
description: '詳細情報: 変数 (Entity SQL)'
title: 変数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 134fee8f61c8e87a18520e6622f6a6a5cceb0076
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795041"
---
# <a name="variables-entity-sql"></a>変数 (Entity SQL)

## <a name="variable"></a>変数  

 変数式は、現在のスコープで定義されている名前付きの式への参照です。 変数参照は、[識別子](identifiers-entity-sql.md)で定義された有効な [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 識別子である必要があります。  
  
 次の例は、式における変数の使用方法を示しています。 FROM 句の `c` は変数の定義です。 SELECT 句内で使用された `c` は、変数参照を表します。  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a>関連項目

- [識別子](identifiers-entity-sql.md)
- [パラメーター](parameters-entity-sql.md)
- [Entity SQL の概要](entity-sql-overview.md)
