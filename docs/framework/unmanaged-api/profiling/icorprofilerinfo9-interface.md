---
title: ICorProfilerInfo9 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 3d1cdfa56e6bb20f08370aa76b87d516f7b51cda
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732958"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9 インターフェイス

複数のネイティブコードバージョンを持つ関数に関する情報を照会するメソッドを提供する [ICorProfilerInfo8](icorprofilerinfo8-interface.md) のサブクラス。  

## <a name="methods"></a>メソッド  

| メソッド|説明|  
| ------------|-----------------|  
|[GetNativeCodeStartAddresses メソッド](icorprofilerinfo9-getnativecodestartaddresses-method.md)| 指定された functionId と rejitId は、現在存在する、このコードのすべての just-in-time バージョンのネイティブコードの開始アドレスを列挙します。 |
|[GetILToNativeMapping3 メソッド](icorprofilerinfo9-getiltonativemapping3-method.md)| ネイティブコードの開始アドレスが指定されている場合、この just-in-time バージョンのコードのネイティブから IL へのマッピング情報を返します。 |
|[GetCodeInfo4 メソッド](icorprofilerinfo9-getcodeinfo4-method.md)| ネイティブコードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。 |

## <a name="requirements"></a>要件  

**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.Net のバージョン:**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
