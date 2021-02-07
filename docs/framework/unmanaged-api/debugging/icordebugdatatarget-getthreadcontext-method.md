---
description: '詳細については、次のページを参照してください: いいね。:: GetThreadContext メソッド'
title: ICorDebugDataTarget::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: cf40579aa0a495af4e5e775334d177ca6f3da86f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710635"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext メソッド

指定されたスレッドの現在のスレッドコンテキストを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwThreadID`  
 からコンテキストを取得するスレッドの識別子。 識別子はオペレーティングシステムによって定義されます。  
  
 `contextFlags`  
 からコンテキストのどの部分を読み取る必要があるかを示す、プラットフォームに依存するフラグのビットごとの組み合わせ。  
  
 `contextSize`  
 [入力] `pContext` のサイズ。  
  
 `pContext`  
 入出力スレッドコンテキストが格納されるバッファー。  
  
## <a name="remarks"></a>解説  

 Windows プラットフォームでは、は、の `pContext` `CONTEXT` 構造体 (winnt.h で定義されています) である必要があります。これは [、の](icordebugdatatarget-getplatform-method.md) 型によって指定されたコンピューターの種類に適しています。 `contextFlags` 構造体のフィールドと同じ値を持つ必要があり `ContextFlags` `CONTEXT` ます。 `CONTEXT`構造体はプロセッサに固有です。詳細については、winnt.h の .h ファイルを参照してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDataTarget インターフェイス](icordebugdatatarget-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
