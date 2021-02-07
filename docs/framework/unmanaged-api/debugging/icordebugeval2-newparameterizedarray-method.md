---
description: '詳細については、次を参照してください: ICorDebugEval2:: NewParameterizedArray メソッド'
title: ICorDebugEval2::NewParameterizedArray メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 0ce8582328013ad02357361f05efb55ade8780e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693747"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray メソッド

指定した要素の型と次元の新しい配列を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pElementType`  
 から配列に格納されている要素の型を表す、の型のオブジェクトへのポインター。  
  
 `rank`  
 から配列の次元数。 .NET Framework バージョン2.0 では、この値は1である必要があります。  
  
 `dims`  
 から配列の各次元のサイズ (バイト単位)。  
  
 `lowBounds`  
 [in] オプション。 配列の各次元の下限。 この値を省略すると、次元ごとに下限0が想定されます。  
  
## <a name="remarks"></a>解説  

 配列の要素は、ジェネリック型のインスタンスである場合があります。 配列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。 .NET Framework 2.0 では、の値は `rank` 1 である必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
