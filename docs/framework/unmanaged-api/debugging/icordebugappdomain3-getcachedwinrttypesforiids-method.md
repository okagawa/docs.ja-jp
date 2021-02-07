---
description: '詳細について: ICorDebugAppDomain3:: GetCachedWinRTTypesForIIDs メソッド'
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 76b93cdb8c465935a4aaf36090ee44f2b6253a3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754174"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド

インターフェイス識別子に基づいて、アプリケーションドメイン内のキャッシュされた Windows ランタイム型の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cReqTypes`  
 から要求される型の数。  
  
 `iidsToResolve`  
 から取得する Windows ランタイム型のマネージ表現に対応するインターフェイス識別子を格納する配列へのポインター。  
  
 `ppTypesEnum`  
 入出力のインターフェイス識別子に基づいて、取得された Windows ランタイム型のキャッシュされたマネージ表現の列挙を可能にする "、"、"" "" ツール "インターフェイスオブジェクトのアドレスへのポインター `iidsToResolve` 。  
  
## <a name="remarks"></a>解説  

 メソッドが特定のインターフェイス識別子に関する情報の取得に失敗した場合、 `ELEMENT_TYPE_END` データの取得に関する問題が原因で、または不明なインターフェイス識別子について、"の型は、" "の種類" になり `ELEMENT_TYPE_VOID` ます。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** Windows ランタイム  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugAppDomain3 インターフェイス](icordebugappdomain3-interface.md)
