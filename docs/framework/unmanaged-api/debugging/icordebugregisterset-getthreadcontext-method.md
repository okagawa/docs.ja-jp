---
description: '詳細については、次のページを参照してください: いいね!:: GetThreadContext メソッド'
title: ICorDebugRegisterSet::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: be6384562858d04b6e139eda83c172c09f2dfc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690796"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a>ICorDebugRegisterSet::GetThreadContext メソッド

現在のスレッドのコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `contextSize`  
 から配列のサイズ (バイト単位) `context` 。  
  
 `context`  
 [入力、出力] `CONTEXT` 現在のプラットフォームの Win32 構造体を構成するバイト配列。  
  
## <a name="remarks"></a>解説  

 `GetThreadContext`スレッドはコンテキストが一時的に変更されている "ハイジャック" 状態になる可能性があるため、デバッガーは Win32 関数の代わりにこの関数を呼び出す必要があります。 返されるデータは、 `CONTEXT` 現在のプラットフォームの Win32 構造体です。  
  
 非リーフフレームの場合、クライアントは、テキストボックス [:: GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md)を使用して、どのレジスタが有効であるかを確認する必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet インターフェイス](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)
