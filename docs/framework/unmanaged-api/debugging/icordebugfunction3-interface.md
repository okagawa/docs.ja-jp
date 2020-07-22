---
title: ICorDebugFunction3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 71aa482cc2268da17f1376d8c305dd6a818d92d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213167"
---
# <a name="icordebugfunction3-interface"></a>ICorDebugFunction3 インターフェイス
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 ICorDebugFunction インターフェイスを論理的に拡張して、ReJIT 要求からコードへのアクセスを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetActiveReJitRequestILCode メソッド](icordebugfunction3-getactiverejitrequestilcode-method.md)|アクティブな ReJIT 要求から IL を含む、[コード](icordebugilcode-interface.md)へのインターフェイスポインターを取得します。|  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
- [ReJIT: ハウツーガイド](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
