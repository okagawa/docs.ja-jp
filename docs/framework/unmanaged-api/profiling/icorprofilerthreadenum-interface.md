---
title: ICorProfilerThreadEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: 147694431d2c378b856577ef5a60e8a8b4e9a7a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721219"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum インターフェイス

共通言語ランタイムのスレッドのコレクションを順番に反復処理するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](icorprofilerthreadenum-clone-method.md)|この `ICorProfilerThreadEnum` インターフェイスのコピーへのインターフェイス ポインターを取得します。|  
|[GetCount メソッド](icorprofilerthreadenum-getcount-method.md)|アプリケーションで使用されるスレッドの数を取得します。|  
|[Next メソッド](icorprofilerthreadenum-next-method.md)|スレッドのシーケンシャル コレクションから、列挙子の現在の位置以降にある指定した数の隣接するスレッドを取得します。|  
|[Reset メソッド](icorprofilerthreadenum-reset-method.md)|列挙子のカーソルをシーケンスの開始位置に移動します。|  
|[Skip メソッド](icorprofilerthreadenum-skip-method.md)|指定した数の要素をスキップするため、この列挙子のカーソルを現在の位置から進めます。|  
  
## <a name="remarks"></a>注釈  

 `ICorProfilerThreadEnum` インターフェイスは列挙子です。 このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。 つまり、受信側は配列要素のフローを明示的に制御できるため、大きな配列をメソッド パラメーターとして渡す場合に関連する問題を回避できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
