---
description: '詳細については、次を参照してください: CorErrorIfEmitOutOfOrder 列挙型'
title: CorErrorIfEmitOutOfOrder 列挙型
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: b45d3204ae386b7ad9d7ab1daccdfdef35e2ad9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784523"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder 列挙型

メタデータの生成順序が不適切である場合にエラー メッセージが生成される条件を示すフラグ値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|エラーメッセージを生成しない既定の動作を示します。|  
|`MDErrorOutOfOrderNone`|コンパイラがエラーメッセージを生成しないことを示します。|  
|`MDErrorOutOfOrderAll`|フィールド、プロパティ、イベント、メソッド、またはパラメーターが順序どおりに生成されない場合に、コンパイラがエラーメッセージを生成することを示します。|  
|`MDMethodOutOfOrder`|メソッドが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。|  
|`MDFieldOutOfOrder`|フィールドが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。|  
|`MDParamOutOfOrder`|パラメーターが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。|  
|`MDPropertyOutOfOrder`|プロパティが順序どおりに出力されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。|  
|`MDEventOutOfOrder`|イベントが順序どおりに生成されない場合に、コンパイラがエラーメッセージを生成する必要があることを示します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorHdr. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
