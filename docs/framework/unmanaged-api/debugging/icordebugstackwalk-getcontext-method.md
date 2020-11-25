---
title: ICorDebugStackWalk::GetContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 927f2077b4bb71177c24816774d06643ebdaa922
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711963"
---
# <a name="icordebugstackwalkgetcontext-method"></a>ICorDebugStackWalk::GetContext メソッド

[は、テキストオブジェクト内](icordebugstackwalk-interface.md)の現在のフレームのコンテキストを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `contextFlags`  
 からコンテキストバッファーの要求されたコンテンツを示すフラグ (Winnt.h で定義されています)。  
  
 `contextBufSize`  
 からコンテキストバッファーに割り当てられたサイズ。  
  
 `contextSize`  
 入出力コンテキストの実際のサイズ。 この値は、コンテキストバッファーのサイズ以下である必要があります。  
  
 `contextBuf`  
 入出力コンテキストバッファー。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|現在のフレームのコンテキストが正常に返されました。|  
|E_FAIL|コンテキストを返すことができませんでした。|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT バッファー)|コンテキストバッファーが小さすぎます。|  
|CORDBG_E_PAST_END_OF_STACK|フレームポインターは既にスタックの末尾にあります。そのため、追加のフレームにアクセスすることはできません。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>解説  

 アンワインドでは、非揮発性レジスタなどのレジスタのサブセットのみが復元されるため、呼び出し時にコンテキストがレジスタの状態と完全に一致するとは限りません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
