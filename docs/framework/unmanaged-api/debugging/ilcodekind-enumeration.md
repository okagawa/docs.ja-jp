---
title: ILCodeKind 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: 7e9cf760ec609786804a05177349ee2eacd79eaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692242"
---
# <a name="ilcodekind-enumeration"></a>ILCodeKind 列挙型

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 デバッガーがローカル変数またはプロファイラー ReJIT インストルメンテーションに追加されたコードにアクセスできるかどうかを指定する値を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー名|説明|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|デバッガーは、ReJIT インストルメンテーションからの情報に対してアクセスできません。|  
|`ILCODE_REJIT_IL`|デバッガーは、ReJIT インストルメンテーションからの情報に対してアクセスできます。|  
  
## <a name="remarks"></a>注釈  

 列挙体のメンバーを `ILCodeKind` [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) メソッドおよび [getlocalvariables ex](icordebugilframe4-getlocalvariableex-method.md) メソッドに渡して、デバッガーがプロファイラー rejit インストルメンテーションに追加された変数にアクセスできるかどうかを判断し、 [getcodeex](icordebugilframe4-getcodeex-method.md) メソッドに渡して、デバッガーがインストルメント化された IL にアクセスできるかどうかを判断できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
- [ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)
- [ReJIT: How-To ガイド](/archive/blogs/davbr/rejit-a-how-to-guide)
