---
description: 詳細については、「ICorProfilerInfo10 インターフェイス」を参照してください。
title: ICorProfilerInfo10 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: fd24491cb1ca55ad48137522c63e78e6387d33e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753290"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 インターフェイス

関数 IL の変更、ランタイムからの情報のクエリ、およびランタイムの中断と再開を行うメソッドを提供する [ICorProfilerInfo9](icorprofilerinfo9-interface.md) のサブクラス。

## <a name="methods"></a>メソッド  

| メソッド|説明|  
| ------------|-----------------|  
|[EnumerateObjectReferences メソッド](icorprofilerinfo10-enumerateobjectreferences-method.md)|ObjectID、callback、および clientData を指定すると、各オブジェクト参照 (存在する場合) が列挙されます。 |
|[IsFrozenObject メソッド](icorprofilerinfo10-isfrozenobject-method.md)|ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。 |
|[GetLOHObjectSizeThreshold メソッド](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|構成された LOH しきい値の値を取得します。 |
|[RequestReJITWithInliners メソッド](icorprofilerinfo10-requestrejitwithinliners-method.md)| 要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。  |
|[SuspendRuntime メソッド](icorprofilerinfo10-suspendruntime-method.md)| GC を実行せずにランタイムを中断します。 |
|[ResumeRuntime メソッド](icorprofilerinfo10-resumeruntime-method.md)| GC を実行せずにランタイムを再開します。 |

## <a name="requirements"></a>要件  

**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
