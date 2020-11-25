---
title: ICorDebug::DebugActiveProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 1713623fa575bea6df649106b37212f7aeaee6db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723468"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess メソッド

デバッガーを既存のプロセスにアタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `id`  
 からデバッガーがアタッチされるプロセスの ID。  
  
 `win32Attach`  
 から `true` デバッガーがプロセスの Win32 デバッガーとして動作し、アンマネージコールバックをディスパッチする場合はに設定されるブール値。それ以外の場合は `false` 。  
  
 `ppProcess`  
 入出力デバッガーがアタッチされているプロセスを表す "いいプロセス" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 相互運用デバッグは、IA-64 ベースおよび AMD64 ベースのプラットフォームなど、Win9x および x86 以外のプラットフォームではサポートされていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
