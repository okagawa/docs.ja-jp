---
description: '詳細について: ICorDebugModule2:: SetJMCStatus メソッド'
title: ICorDebugModule2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: 7d91d098c21eac39d18a0aa7c3d4fd795be509ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790803"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus メソッド

この ICorDebugModule2 内のすべてのクラスのすべてのメソッドのマイコードのみ (JMC) の状態を、指定した値に設定し `pTokens` ます。ただし、逆の値に設定されている配列内のすべてのメソッドを除きます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bIsJustMycode`  
 からコードを `true` デバッグする場合はに設定し、それ以外の場合はに設定 `false` します。  
  
 `cTokens`  
 [in] `pTokens` 配列のサイズ。  
  
 `pTokens`  
 から値の配列 `mdToken` 。各値は、JMC の状態が! に設定されるメソッドを参照し `bIsJustMycode` ます。  
  
## <a name="remarks"></a>解説  

 配列に指定されている各メソッドの JMC の状態 `pTokens` は、値の逆に設定され `bIsJustMycode` ます。 このモジュール内の他のすべてのメソッドの状態は、値に設定され `bIsJustMycode` ます。  
  
 メソッドは、 `SetJMCStatus` このモジュール内の以前のすべての JMC 設定を消去します。  
  
 `SetJMCStatus`すべての関数が正常に設定されている場合、メソッドは S_OK HRESULT を返します。 マークされている一部の関数がデバッグ可能でない場合は、CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT が返され `true` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
