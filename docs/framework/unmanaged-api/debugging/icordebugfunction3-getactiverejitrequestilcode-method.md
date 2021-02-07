---
description: '詳細について: ICorDebugFunction3:: GetActiveReJitRequestILCode メソッド'
title: ICorDebugFunction3::GetActiveReJitRequestILCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 9225c5cdf97395b7e1b11c61d653cab8d52031c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692122"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>ICorDebugFunction3::GetActiveReJitRequestILCode メソッド

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 アクティブな ReJIT 要求から IL を含む、 [コード](icordebugilcode-interface.md) へのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppReJitedILCode`  
 アクティブな ReJIT 要求からの、IL へのポインター。  
  
## <a name="remarks"></a>解説  

 この `ICorDebugFunction3` オブジェクトによって表示されるメソッドがアクティブな ReJIT 要求を持っている場合、`ppReJitedILCode` は IL へのポインターを返します。 一般的なケースであるアクティブな要求がない場合、 `ppReJitedILCode` は **null** になります。  
  
 ReJIT 要求は、 [ICorProfilerCallback4:: GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) メソッドの呼び出しから実行が戻った直後にアクティブになります。 これは、まだ JIT コンパイルされていない可能性があり、スレッドはコードの元のバージョンで実行中の可能性があります。 ReJIT 要求は、 [ICorProfilerInfo4:: RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) メソッドへのプロファイラーの呼び出し中に非アクティブになります。 LI が戻された後であっても、スレッドは JIT 再コンパイル (ReJIT) されたコードで実行中の可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugFunction3 インターフェイス](icordebugfunction3-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [ReJIT: How-To ガイド](/archive/blogs/davbr/rejit-a-how-to-guide)
