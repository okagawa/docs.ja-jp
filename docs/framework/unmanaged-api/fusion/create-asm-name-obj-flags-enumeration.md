---
description: '詳細情報: CREATE_ASM_NAME_OBJ_FLAGS 列挙型'
title: CREATE_ASM_NAME_OBJ_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: b68eed0671d57893e7ffbfbd8127c7ef872d5eb0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761201"
---
# <a name="create_asm_name_obj_flags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS 列挙型

[Createassemblynameobject](createassemblynameobject-function.md)関数によって構築されるときに、 [IAssemblyName Interface](iassemblyname-interface.md)オブジェクトの属性を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|渡されたパラメーターがテキスト形式の id であることを示します。|  
|`CANOF_SET_DEFAULT_VALUES`|いくつかの既定値を設定します。|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|フレンドアセンブリの規則 (名前と公開キーのみ) を確認します。 このメンバーは内部でのみ使用されます。|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|`CANOF_PARSE_DISPLAY_NAME`フラグとフラグの組み合わせ `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` 。 このメンバーは内部でのみ使用されます。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyName インターフェイス](iassemblyname-interface.md)
- [CreateAssemblyNameObject 関数](createassemblynameobject-function.md)
- [fusion 列挙体](fusion-enumerations.md)
