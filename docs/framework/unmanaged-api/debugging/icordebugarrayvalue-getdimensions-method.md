---
title: ICorDebugArrayValue::GetDimensions メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: bf498a14af3dccc7278155ecfc74132c2b519ed3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698196"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a>ICorDebugArrayValue::GetDimensions メソッド

この配列の各次元に含まれる要素の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cdim`  
 からこの ICorDebugArrayValue オブジェクトの次元数。  
  
 この値は、 `dims` 配列のサイズがオブジェクトの次元数と同じであるため、配列のサイズでも `ICorDebugArrayValue` あります。  
  
 `dims`  
 入出力整数の配列。各整数は、このオブジェクト内のディメンション内の要素の数を指定し `ICorDebugArrayValue` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
