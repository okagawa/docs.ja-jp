---
description: 詳細については、「ICorProfilerModuleEnum インターフェイス」を参照してください。
title: ICorProfilerModuleEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 195379e9ad6bce94fc93465fe5e1418c5d8c076d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783821"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum インターフェイス

アプリケーションまたはプロファイラーによってロードされたモジュールのコレクションを順番に反復処理するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](icorprofilermoduleenum-clone-method.md)|この `ICorProfilerModuleEnum` インターフェイスのコピーへのインターフェイス ポインターを取得します。|  
|[GetCount メソッド](icorprofilermoduleenum-getcount-method.md)|アプリケーションによって読み込まれたマネージド モジュールの数を取得します。|  
|[次のメソッド](icorprofilermoduleenum-next-method.md)|オブジェクトのシーケンシャル コレクションから、列挙子の現在の位置以降にある指定した数の隣接するモジュールを取得します。|  
|[Reset メソッド](icorprofilermoduleenum-reset-method.md)|列挙子のカーソルをシーケンスの開始位置に移動します。|  
|[Skip メソッド](icorprofilermoduleenum-skip-method.md)|指定した数の要素がスキップされるように、この列挙子のカーソルの位置を進めます。|  
  
## <a name="remarks"></a>解説  

 `ICorProfilerModuleEnum` インターフェイスは列挙子です。 このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。 つまり、受信側は配列要素のフローを明示的に制御できるため、大きな配列をメソッド パラメーターとして渡す場合に関連する問題を回避できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [EnumModules メソッド](icorprofilerinfo3-enummodules-method.md)
