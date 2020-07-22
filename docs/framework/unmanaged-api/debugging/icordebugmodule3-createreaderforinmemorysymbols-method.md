---
title: ICorDebugModule3::CreateReaderForInMemorySymbols メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 2a8200f942405395429db182b7501a07fc1f930a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212322"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols メソッド
動的モジュールのデバッグシンボルリーダーを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>パラメーター  
 riid  
 から返す COM インターフェイスの IID。 通常、これは[ISymUnmanagedReader インターフェイス](../diagnostics/isymunmanagedreader-interface.md)です。  
  
 ppObj  
 入出力返されたインターフェイスへのポインターへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 リーダーが正常に作成されました。  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 モジュールがメモリ内または動的モジュールではありません。  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 シンボルは、アプリケーションによって提供されていないか、まだ使用できません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 リーダーを作成できません。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを使用して、インメモリ (非動的) モジュール用のシンボルリーダーオブジェクトを作成することもできますが、最初にシンボルを使用できるようになった後 ( [UpdateModuleSymbols メソッド](icordebugmanagedcallback-updatemodulesymbols-method.md)コールバックによって示されます) にのみ使用できます。  
  
 このメソッドは、呼び出されるたびに新しいリーダーインスタンスを返します ( [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)など)。 したがって、デバッガーは、基になるデータが変更されている (つまり、 [Loadclass メソッド](icordebugmanagedcallback-loadclass-method.md)のコールバックが受信された) 場合にのみ、結果をキャッシュし、新しいインスタンスを要求します。  
  
 動的モジュールでは、最初の型が読み込まれるまで ( [Loadclass メソッド](icordebugmanagedcallback-loadclass-method.md)コールバックによって示されるように) シンボルは使用できません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemoteTarget インターフェイス](icordebugremotetarget-interface.md)
- [ICorDebug インターフェイス](icordebug-interface.md)

- [デバッグのインターフェイス](debugging-interfaces.md)
