---
title: ICLRDebugging::CanUnloadNow メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: e89d936c528ea7482487a8629dbd882f6f67483e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723572"
---
# <a name="iclrdebuggingcanunloadnow-method"></a>ICLRDebugging::CanUnloadNow メソッド

[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)インターフェイスによって提供されたライブラリがまだ使用中であるか、またはアンロードできるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a>パラメーター  

 `hmodule`  
 からターゲットプロセス内のモジュールのベースアドレス。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|によって参照されているモジュールは、 `hmodule` アンロードできます。|  
|S_FALSE|によって参照されているモジュール `hmodule` は、引き続き使用されています。|  
|COR_E_NOT_CLR|指定されたモジュールは CLR モジュールではありません。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>解説  

 このメソッドは、インターフェイスのすべてのインスタンスが解放されているかどうかを確認し、 `ICorDebug*` 現在 [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) メソッドの呼び出し内にスレッドが存在しないかどうかを確認します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
