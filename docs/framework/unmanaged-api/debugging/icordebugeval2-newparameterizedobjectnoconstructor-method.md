---
description: '詳細について: ICorDebugEval2:: NewParameterizedObjectNoConstructor メソッド'
title: ICorDebugEval2::NewParameterizedObjectNoConstructor メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 8300378facb38714b50d6507b19876b8721c6229
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693591"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor メソッド

コンストラクターメソッドを呼び出さずに、指定したクラスの新しいパラメーター化された型オブジェクトをインスタンス化します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pClass`  
 からインスタンス化するオブジェクトのクラスを表す、のオブジェクトへのポインター。  
  
 `nTypeArgs`  
 から渡された型引数の数。  
  
 `ppTypeArgs`  
 からポインターの配列。各ポインターは、インスタンス化されているオブジェクトの型引数を表す、テキスト型のオブジェクトを指します。  
  
## <a name="remarks"></a>解説  

 `NewParameterizedObjectNoConstructor`型引数の数が正しくないか、型引数の型が正しくない場合、メソッドは失敗します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
