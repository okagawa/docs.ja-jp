---
title: ICorDebugCode3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: 6f66e4a903be2e9b12a573f74638a62c58005689
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893454"
---
# <a name="icordebugcode3-interface"></a>ICorDebugCode3 インターフェイス
"" のコード "と" ICorDebugCode2 "を拡張して、マネージ戻り値に関する情報を提供するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReturnValueLiveOffset メソッド](icordebugcode3-getreturnvalueliveoffset-method.md)|指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugILFrame3 インターフェイス](icordebugilframe3-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
