---
description: '詳細について: ICLRDataEnumMemoryRegions:: EnumMemoryRegions メソッド'
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: 48887defab38d6ac99c718e14646d39166927438
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785732"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions メソッド

指定されたメモリ領域を列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `callback`  
 から結果をデバッガーに通知するために、列挙される各メモリ領域に対してこのメソッドによって呼び出される [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) インスタンスへのポインター。  
  
 コールバックがエラーを示す場合でも、メモリ領域の列挙は続行されます。  
  
 `miniDumpFlags`  
 から使用しません。  
  
 `clrFlags`  
 から列挙するメモリ領域を指定する [Clrdataenummemoryflags](clrdataenummemoryflags-enumeration.md) 列挙体の値。  
  
## <a name="remarks"></a>解説  

 このメソッドは、指定された [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) インスタンスを使用して、結果を呼び出し元に通知します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataEnumMemoryRegions インターフェイス](iclrdataenummemoryregions-interface.md)
