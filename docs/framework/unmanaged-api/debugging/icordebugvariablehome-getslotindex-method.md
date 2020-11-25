---
title: 'いい変数 Home:: GetSlotIndex メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 4b071bd8e9d96084848c1553385eec5f8beca624
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711729"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>いい変数 Home:: GetSlotIndex メソッド

ローカル変数のマネージドスロットインデックスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pSlotIndex`  
 入出力ローカル変数のスロットインデックスへのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドは、次の値を返します。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッド呼び出しによって、でスロットインデックス値が返されました `pSlotIndex` 。|  
|`E_FAIL`|現在のは、 [関数の引数](icordebugvariablehome-interface.md) を表します。|  
  
## <a name="remarks"></a>注釈  

 このローカル変数のメタデータを取得するために、スロットインデックスを使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugVariableHome インターフェイス](icordebugvariablehome-interface.md)
