---
title: ICorDebugAppDomain::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 501a4543940437bfe2a6cb0952aed8184107150c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672163"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName メソッド

アプリケーションドメインの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cchName`  
 [in] `szName` 配列のサイズ。 このメソッドをクエリモードにするには、この値を0に設定します。  
  
 `pcchName`  
 入出力名前のサイズ、またはで実際に返された文字数へのポインター `szName` 。 クエリモードでは、この値によって、呼び出し元は、名前に割り当てるバッファーの大きさを知ることができます。  
  
 `szName`  
 入出力アプリケーションドメインの名前を格納する配列。  
  
## <a name="remarks"></a>注釈  

 デバッガーは、 `GetName` メソッドを1回呼び出して、名前に必要なバッファーのサイズを取得します。 デバッガーによってバッファーが割り当てられ、メソッドが2回目に呼び出されてバッファーに格納されます。 名前のサイズを取得するための最初の呼び出しは、 *クエリモード* と呼ばれます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
