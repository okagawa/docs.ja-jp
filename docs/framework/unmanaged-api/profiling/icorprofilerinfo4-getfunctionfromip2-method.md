---
description: '詳細について: ICorProfilerInfo4:: GetFunctionFromIP2 メソッド'
title: ICorProfilerInfo4::GetFunctionFromIP2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: f6abda7c9e7d4abcc0f0b256d6a7785cea205d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686805"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 メソッド

マネージコード命令ポインターを JIT 再コンパイルされた関数のバージョンにマップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ip`  
 からマネージコード内の命令ポインター。  
  
 `pFunctionId`  
 入出力関数 ID。  
  
 `pReJitId`  
 入出力関数の JIT 再コンパイルバージョンの id。  
  
## <a name="remarks"></a>解説  

 `GetFunctionFromIP2` はと似てい `GetFunctionFromIP` ますが、指定された IP アドレスを含む関数の関数 id ではなく、JIT 再コンパイルされた id を取得する点が異なります。  
  
> [!NOTE]
> `GetFunctionFromIP2` はガベージコレクションをトリガーできますが、で `GetFunctionFromIP` は発生しません。  詳細については、「 [HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md)」を参照してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
