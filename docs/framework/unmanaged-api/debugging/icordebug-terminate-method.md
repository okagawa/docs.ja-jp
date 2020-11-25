---
title: ICorDebug::Terminate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: cf9c9d11c4725908fcf7ff4a0c91882b70a80190
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723377"
---
# <a name="icordebugterminate-method"></a>ICorDebug::Terminate メソッド

オブジェクトを終了 `ICorDebug` します。  
  
> [!NOTE]
> `Terminate` デバッグされているすべてのプロセスに対して、 [ExitProcess Callback callback::](icordebugmanagedcallback-exitprocess-method.md) callback が受信されるまでは呼び出さないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a>解説  

 `Terminate` オブジェクトが不要になった場合は、を呼び出す必要があり `ICorDebug` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
