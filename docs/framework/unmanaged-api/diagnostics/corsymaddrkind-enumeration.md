---
title: CorSymAddrKind 列挙体
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: 5991b0abaedabe2337cd754c7bd19f96c5e9b685
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420618"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind 列挙体
メモリアドレスの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Microsoft 中間言語 (MSIL) のローカル変数またはパラメーターインデックスを示します。|  
|`ADDR_NATIVE_RVA`|モジュール内の相対仮想アドレスを示します。|  
|`ADDR_NATIVE_REGISTER`|CPU レジスタを示します。|  
|`ADDR_NATIVE_REGREL`|は、最初のアドレスがレジスタで、2番目のアドレスがオフセットであることを示します。|  
|`ADDR_NATIVE_OFFSET`|ベースアドレスからのオフセットを示します。|  
|`ADDR_NATIVE_REGREG`|最初のアドレスがレジスタの低い部分であり、2番目のアドレスが上位部分であることを示します。|  
|`ADDR_NATIVE_REGSTK`|最初のアドレスがレジスタの下位にあり、2番目が上位の部分、3番目のアドレスがオフセットであることを示します。|  
|`ADDR_NATIVE_STKREG`|は、最初のアドレスがレジスタ、2番目のアドレスがオフセット、3番目がレジスタの上位部分であることを示します。|  
|`ADDR_BITFIELD`|最初のアドレスがフィールドの先頭で、2番目のアドレスがフィールド長であることを示します。|  
|`ADDR_NATIVE_ISECTOFFSET`|は、最初のアドレスがセクションで、2番目のアドレスがオフセットであることを示します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断列挙型](diagnostics-symbol-store-enumerations.md)
