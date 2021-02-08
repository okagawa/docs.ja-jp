---
description: '詳細については、次の情報を参照してください: いいね:: GetXML メソッド'
title: ICorDebugMDA::GetXML メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: fa506e6e8f306271f10a7a715af9b8bc6a80c1d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801138"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML メソッド

[によって](icordebugmda-interface.md)表されるマネージデバッグアシスタント (MDA) に関連付けられた完全な XML ストリームを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cchName`  
 [in] `szName` 配列のサイズ。  
  
 `pcchName`  
 入出力XML ストリームの長さへのポインター。  
  
 `szName`  
 入出力XML ストリームを格納する配列。 配列が空である可能性があります。  
  
## <a name="remarks"></a>解説  

 メソッドは、 `GetXML` 関連付けられている XML ストリームのサイズによっては、パフォーマンスに影響を与える可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMDA インターフェイス](icordebugmda-interface.md)
- [マネージド デバッグ アシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
