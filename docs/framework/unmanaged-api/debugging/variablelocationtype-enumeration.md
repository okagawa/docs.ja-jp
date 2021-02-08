---
description: '詳細については、次を参照してください: VariableLocationType 列挙型'
title: VariableLocationType 列挙型
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: 8561077b9f3f4d318eeb743d51538b2a9a22a217
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800527"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType 列挙型

変数のネイティブな場所の種類を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`VLT_REGISTER`|変数はレジスタにあります。|  
|`VLT_REGISTER_RELATIVE`|変数は、レジスタ相対メモリの場所にあります。|  
|`VLT_INVALID`|変数はレジスタまたはレジスタの相対メモリ位置に格納されません。|  
  
## <a name="remarks"></a>解説  

 列挙体のメンバー `VariableLocationType` は、 [GetLocationType](icordebugvariablehome-getlocationtype-method.md) メソッドによって返されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
