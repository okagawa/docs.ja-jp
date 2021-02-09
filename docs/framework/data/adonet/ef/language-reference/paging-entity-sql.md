---
description: '詳細情報: ページング (Entity SQL)'
title: ページング (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: c32474b772be359dbf2ffd46e5489cc0b4b2abb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791856"
---
# <a name="paging-entity-sql"></a>ページング (Entity SQL)

物理的なページングは、[ORDER BY](order-by-entity-sql.md) 句の [SKIP](skip-entity-sql.md) サブ句および [LIMIT](limit-entity-sql.md) サブ句を使用して実行できます。 物理的ページングを決定的に実行するには、SKIP と LIMIT を使用する必要があります。 非決定的な方法で結果の行の数を制限するには、[TOP](top-entity-sql.md) を使用する必要があります。 TOP および SKIP/LIMIT は、同時には指定できません。  
  
## <a name="top-overview"></a>TOP の概要  

 SELECT 句には、オプションの ALL/DISTINCT 修飾子に続けてオプションの TOP サブ句を指定できます。 TOP サブ句は、クエリ結果の先頭から指定した行セットだけを返すよう指定します。 詳細については、「[TOP](top-entity-sql.md)」を参照してください。  
  
## <a name="skip-and-limit-overview"></a>SKIP/LIMIT の概要  

 SKIP と LIMIT は ORDER BY 句の一部です。 SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。 たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。 LIMIT 式のサブ句が ORDER BY 句に存在する場合、クエリは並べ替え順序に従って並べ替えられ、結果の行数は LIMIT 式によって制限されます。 たとえば、LIMIT 5 は、結果セットを 5 つのインスタンスまたは行に制限します。 SKIP と LIMIT を同時に使用することはできません。SKIP のみまたは LIMIT のみを ORDER BY 句と一緒に使用できます。 詳細については、次のトピックを参照してください。  
  
- [SKIP](skip-entity-sql.md)  
  
- [LIMIT](limit-entity-sql.md)  
  
- [ORDER BY](order-by-entity-sql.md)  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [Entity SQL の概要](entity-sql-overview.md)
- [方法: クエリの結果をページングする](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
