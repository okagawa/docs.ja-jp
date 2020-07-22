---
title: ICoreClrDebugTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: c44a12ef377d29e0b33b8be86aa1d8f0aa9d26bd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397151"
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget インターフェイス
参照カウントを制御し、プロセスを列挙し、リモートの Macintosh Silverlight ターゲットにアタッチされているデバッガーに関連付けられているメモリを解放するメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ICoreClrDebugTarget::EnumProcesses メソッド](icoreclrdebugtarget-enumprocesses-method.md)|リモート コンピューターで実行されているプロセスを列挙します。|  
|[ICoreClrDebugTarget::EnumRuntimes メソッド](icoreclrdebugtarget-enumruntimes-method.md)|リモートコンピューター上の指定されたプロセスの共通言語ランタイム (CLRs) を列挙します。|  
|[ICoreClrDebugTarget::FreeMemory メソッド](icoreclrdebugtarget-freememory-method.md)|このクラスの列挙メソッドによって割り当てられたメモリを解放します。|  
  
## <a name="remarks"></a>解説  
 現在、この機能は、リモートの Macintosh コンピューターで実行されている Silverlight ベースのアプリケーションターゲットをデバッグする場合にのみサポートされます。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Coreclrremoteデバッグインターフェイス .h  
  
 **Library:** mscordbi_macx86 .dll  
  
 **.NET Framework のバージョン:** 3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemoteTarget インターフェイス](icordebugremotetarget-interface.md)
- [ICorDebug インターフェイス](icordebug-interface.md)

- [デバッグのインターフェイス](debugging-interfaces.md)
