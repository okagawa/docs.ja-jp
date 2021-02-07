---
description: '詳細について: ICorDebugEval2:: NewParameterizedObject メソッド'
title: ICorDebugEval2::NewParameterizedObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
ms.openlocfilehash: 2dc746fdada0e79044a1387bd4cb1c11b81d7777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693682"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject メソッド

新しいパラメーター化された型オブジェクトをインスタンス化し、オブジェクトのコンストラクターメソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pConstructor`  
 からインスタンス化するオブジェクトのコンストラクターを表す、のオブジェクトへのポインター。  
  
 `nTypeArgs`  
 から渡された型引数の数。  
  
 `ppTypeArgs`  
 からポインターの配列。各ポインターは、インスタンス化されているオブジェクトの型引数を表す、テキスト型のオブジェクトを指します。  
  
 `nArgs`  
 からコンストラクターに渡された引数の数。  
  
 `ppArgs`  
 からポインターの配列。各ポインターは、コンストラクターに渡される引数値を表す ICorDebugValue オブジェクトを指します。  
  
## <a name="remarks"></a>解説  

 オブジェクトのコンストラクターは、パラメーターを受け取ることができ <xref:System.Type> ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
