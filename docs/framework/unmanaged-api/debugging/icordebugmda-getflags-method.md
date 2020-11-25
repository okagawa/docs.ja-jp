---
title: ICorDebugMDA::GetFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 38a5c2da900530b6bf78f24e224714496ceaa62c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710962"
---
# <a name="icordebugmdagetflags-method"></a>ICorDebugMDA::GetFlags メソッド

によって表されるマネージデバッグアシスタント (MDA) に関連付けら [れている](icordebugmda-interface.md)フラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pFlags`  
 からこの MDA のフラグの設定を指定する [Cordebugmdaflags](cordebugmdaflags-enumeration.md) 列挙値のビットごとの組み合わせ。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMDA インターフェイス](icordebugmda-interface.md)
- [マネージド デバッグ アシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
