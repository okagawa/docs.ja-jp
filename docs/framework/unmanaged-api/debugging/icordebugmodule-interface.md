---
title: ICorDebugModule インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212244"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule インターフェイス

実行可能ファイルまたはダイナミックリンクライブラリ (DLL) のいずれかである共通言語ランタイム (CLR) モジュールを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](icordebugmodule-createbreakpoint-method.md)|実装されていません。|  
|[EnableClassLoadCallbacks メソッド](icordebugmodule-enableclassloadcallbacks-method.md)|このモジュールに対して、" [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) " コール[バック:: loadclass](icordebugmanagedcallback-loadclass-method.md)との各コールバックを呼び出すかどうかを決定します。|  
|[EnableJITDebugging メソッド](icordebugmodule-enablejitdebugging-method.md)|Just-in-time (JIT) コンパイラが、このモジュール内のメソッドのデバッグ情報を保持するかどうかを決定します。|  
|[GetAssembly メソッド](icordebugmodule-getassembly-method.md)|このモジュールの格納アセンブリを取得します。|  
|[GetBaseAddress メソッド](icordebugmodule-getbaseaddress-method.md)|モジュールのベースアドレスを取得します。|  
|[GetClassFromToken メソッド](icordebugmodule-getclassfromtoken-method.md)|メタデータから、このクラスを取得します。|  
|[GetEditAndContinueSnapshot メソッド](icordebugmodule-geteditandcontinuesnapshot-method.md)|非推奨になりました。|  
|[GetFunctionFromRVA メソッド](icordebugmodule-getfunctionfromrva-method.md)|実装されていません。|  
|[GetFunctionFromToken メソッド](icordebugmodule-getfunctionfromtoken-method.md)|メタデータトークンによって指定された関数を取得します。|  
|[GetGlobalVariableValue メソッド](icordebugmodule-getglobalvariablevalue-method.md)|指定したグローバル変数の値オブジェクトを取得します。|  
|[GetMetaDataInterface メソッド](icordebugmodule-getmetadatainterface-method.md)|モジュールのメタデータを調べるために使用できるメタデータインターフェイスポインターを取得します。|  
|[GetName メソッド](icordebugmodule-getname-method.md)|モジュールのファイル名を取得します。|  
|[GetProcess メソッド](icordebugmodule-getprocess-method.md)|このモジュールの格納プロセスを取得します。|  
|[GetSize メソッド](icordebugmodule-getsize-method.md)|モジュールのサイズ (バイト単位) を取得します。|  
|[GetToken メソッド](icordebugmodule-gettoken-method.md)|このモジュールのテーブルエントリのトークンを取得します。|  
|[IsDynamic メソッド](icordebugmodule-isdynamic-method.md)|モジュールが動的かどうかを示します。|  
|[IsInMemory メソッド](icordebugmodule-isinmemory-method.md)|このモジュールがメモリ内にのみ存在するかどうかを示します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
