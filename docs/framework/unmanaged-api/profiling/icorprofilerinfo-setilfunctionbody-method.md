---
title: ICorProfilerInfo::SetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 462fc7222243f8cad4e1d03d1717eedace549836
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502939"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a>ICorProfilerInfo::SetILFunctionBody メソッド
指定したモジュール内の指定した関数の本体を置き換えます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleId`  
 から関数が存在するモジュールの ID。  
  
 `methodid`  
 から本文の置換対象となる関数のトークン。  
  
 `pbNewILMethodHeader`  
 から関数の新しいヘッダー。  
  
## <a name="remarks"></a>解説  
 メソッドは、 `SetILFunctionBody` メタデータ内の関数の相対仮想アドレスを置き換えて、新しい関数本体をポイントし、必要に応じて内部データ構造を調整します。  
  
 メソッドは、 `SetILFunctionBody` just-in-time (JIT) コンパイラによってコンパイルされたことがない関数に対してのみ呼び出すことができます。  
  
 [ICorProfilerInfo:: GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)メソッドを使用して、新しいメソッドの領域を割り当て、バッファーに互換性があることを確認します。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
