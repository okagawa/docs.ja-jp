---
description: '詳細情報: ビット単位の正規関数'
title: ビット単位の正規関数
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: a811c707749af2d2fa9472ae2d1444c3f076aeec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697102"
---
# <a name="bitwise-canonical-functions"></a>ビット単位の正規関数

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] にはビット単位の正規関数があります。  
  
## <a name="remarks"></a>Remarks  

 次の表に、ビット単位の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数を示します。 `Null` が入力された場合、これらの関数では `Null` が返されます。 戻り値の型は、引数の型と同じです。 複数の引数を関数が受け取る場合、それらの引数は同じ型にする必要があります。 異なる型でビット単位の演算を実行するには、明示的に同じ型にキャストする必要があります。  
  
|関数|説明|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|`value1` と `value2` のビット単位の論理積を `value1` と `value2` の型で返します。<br /><br /> **引数**<br /><br /> `Byte`、`Int16`、`Int32`、および `Int64`。<br /><br /> **例**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|`value` のビット単位の否定を返します。<br /><br /> **引数**<br /><br /> `Byte`、`Int16`、`Int32`、および `Int64`。<br /><br /> **例**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|`value1` と `value2` のビット単位の論理和を `value1` と `value2` の型で返します。<br /><br /> **引数**<br /><br /> `Byte`、`Int16`、`Int32`、および `Int64`。<br /><br /> **例**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|`value1` と `value2` のビット単位の排他的論理和を `value1` と `value2` の型で返します。<br /><br /> **引数**<br /><br /> `Byte`、`Int16`、`Int32`、および `Int64`。<br /><br /> **例**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>関連項目

- [正規関数](canonical-functions.md)
