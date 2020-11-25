---
title: ICorDebugEval2::CallParameterizedFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: c36dec80b6885b0ee56670b94dbd0b155a9710b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729708"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction メソッド

指定されたは、コンストラクターがパラメーターを受け取るクラス内で入れ子にすることができます <xref:System.Type> 。また、パラメーターを受け取ることもできます <xref:System.Type> 。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pFunction`  
 から呼び出される関数を `ICorDebugFunction` 表すオブジェクトへのポインター。  
  
 `nTypeArgs`  
 から関数が受け取る引数の数。  
  
 `ppTypeArgs`  
 からポインターの配列。各ポインターは、関数の引数を表す、テキストオブジェクトを指します。  
  
 `nArgs`  
 から関数で渡される値の数。  
  
 `ppArgs`  
 からポインターの配列。各ポインターは、関数の引数で渡された値を表す ICorDebugValue オブジェクトを指します。  
  
## <a name="remarks"></a>注釈  

 `CallParameterizedFunction`は、関数が型パラメーターを持つクラス内に存在しても、それ自体が型パラメーターを受け取る可能性があるか、またはその両方であるかを除いて、のように[します。](icordebugeval-callfunction-method.md) 型引数は、クラスに対して最初に指定する必要があります。その後、関数に対して指定する必要があります。  
  
 関数が別のアプリケーションドメインにある場合は、遷移が発生します。 ただし、すべての型引数と値引数は、ターゲットアプリケーションドメインに存在する必要があります。  
  
 関数の評価は、限られたシナリオでのみ実行できます。 `CallParameterizedFunction`または `ICorDebugEval::CallFunction` が失敗した場合、返される HRESULT は失敗の最も一般的な原因を示します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
