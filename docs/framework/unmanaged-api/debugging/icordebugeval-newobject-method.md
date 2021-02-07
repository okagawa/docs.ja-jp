---
description: '詳細については、次を参照してください: いいね:: NewObject メソッド'
title: ICorDebugEval::NewObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: 0f7feb53d061e5dbc453015772b97f2a5a59bbb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693955"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject メソッド

新しいオブジェクトインスタンスを割り当て、指定したコンストラクターメソッドを呼び出します。  
  
 このメソッドは .NET Framework バージョン2.0 では廃止されています。 代わりに [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) を使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pConstructor`  
 から呼び出されるコンストラクター。  
  
 `nArgs`  
 [in] `ppArgs` 配列のサイズ。  
  
 `ppArgs`  
 からICorDebugValue オブジェクトの配列。各オブジェクトは、コンストラクターに渡される引数を表します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** 1.1、1.0  
  
## <a name="see-also"></a>関連項目

- [NewParameterizedObject メソッド](icordebugeval2-newparameterizedobject-method.md)
