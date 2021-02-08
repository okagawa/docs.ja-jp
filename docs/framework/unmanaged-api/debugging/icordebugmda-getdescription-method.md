---
description: '詳細については、次のページを参照してください: いいね:: GetDescription メソッド'
title: ICorDebugMDA::GetDescription メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
ms.openlocfilehash: 75ee7d0b912c9f0039acc872173f2cbad25fff38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801203"
---
# <a name="icordebugmdagetdescription-method"></a>ICorDebugMDA::GetDescription メソッド

によって表されるマネージデバッグアシスタント (MDA) の説明を含む文字列を [取得します](icordebugmda-interface.md)。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cchName`  
 から説明を格納する文字列バッファーのサイズ。  
  
 `pcchName`  
 入出力文字列バッファーで返されたバイト数へのポインター。  
  
 `szName`  
 入出力MDA の説明を格納している文字列バッファー。  
  
## <a name="remarks"></a>解説  

 文字列の長さは0にすることができます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMDA インターフェイス](icordebugmda-interface.md)
- [マネージド デバッグ アシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
