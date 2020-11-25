---
title: ICorDebugAppDomain2::GetArrayOrPointerType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: 8b3f6ae92e39f5385bf29f8b29abbb1726136088
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724768"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType メソッド

指定した型、または指定した型へのポインターまたは参照の配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `elementType`  
 から作成する基になるネイティブ型 (配列、ポインター、または参照) を指定する CorElementType 列挙体の値。  
  
 `nRank`  
 から配列のランク (次元の数)。 が `elementType` ポインターまたは参照型を指定する場合、この値は0である必要があります。  
  
 `pTypeArg`  
 から作成される配列、ポインター、または参照の型を表す、の型のオブジェクトへのポインター。  
  
 `ppType`  
 入出力構築された `ICorDebugType` 配列、ポインター型、または参照型を表すオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 *ElementType* の値には、次のいずれかを指定する必要があります。  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY または ELEMENT_TYPE_SZARRAY  
  
 *ElementType* の値が ELEMENT_TYPE_PTR または ELEMENT_TYPE_BYREF の場合、 *n ランク* は0にする必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
