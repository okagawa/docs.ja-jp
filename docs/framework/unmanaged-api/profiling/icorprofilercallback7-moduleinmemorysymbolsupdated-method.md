---
description: '詳細については、次を参照してください: ICorProfilerCallback7:: Moduleinmemoryシンボル Supmethod'
title: 'ICorProfilerCallback7:: Moduleinmemory メソッド'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: 74adf7edc5269824a924933eb3284a5964e1bac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781728"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7:: Moduleinmemory メソッド

[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 メモリ内モジュールに関連付けられているシンボルストリームが更新されるたびに、プロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 [入力] `moduleId`  
 シンボルストリームが更新されるメモリ内モジュールの識別子。  
  
## <a name="remarks"></a>解説  

 このコールバックは、 [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドを呼び出すときに、 [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md)イベントマスクフラグを設定することによって制御されます。  
  
> [!NOTE]
> このイベントは、api を使用して暗黙的に作成または変更されたシンボルに対しては、現在発生していません <xref:System.Reflection.Emit> 。  
  
 アセンブリのシンボルを指定する引数を含むマネージメソッドのオーバーロードのいずれかを呼び出すことによって、シンボルが事前に提供されていても <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> `rawSymbolStore` 、 [moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) コールバックが発生するまで、ランタイムはシンボリックデータをモジュールに実際に関連付けない場合があります。 このイベントは、後でこのようなモジュールのシンボルを収集する機会を提供します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ModuleLoadFinished メソッド](icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 メソッド](icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 インターフェイス](icorprofilercallback7-interface.md)
