---
description: '詳細情報: ICorDebugAppDomainEnum:: Next メソッド'
title: ICorDebugAppDomainEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: ac5397250e661b4ed380b3272744957f86e1a07b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791531"
---
# <a name="icordebugappdomainenumnext-method"></a>ICorDebugAppDomainEnum::Next メソッド

現在のカーソル位置から開始して、指定した数のアプリケーションドメインをコレクションから取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `celt`  
 から取得するアプリケーションドメインの数。  
  
 `values`  
 入出力ポインターの配列。各ポインターは、アプリケーションドメインを表す、の各オブジェクトを指します。  
  
 `pceltFetched`  
 入出力実際に返されたアプリケーションドメインの数へのポインター。 が1の場合、この値は null `celt` になります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
