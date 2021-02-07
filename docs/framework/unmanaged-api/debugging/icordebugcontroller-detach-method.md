---
description: '詳細については、次の情報を参照してください: いいね::D etach メソッド'
title: ICorDebugController::Detach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: 763386fa72fab023becf4a360556e61d500c7949
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764651"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach メソッド

プロセスまたはアプリケーションドメインからデバッガーをデタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>解説  

 プロセスまたはアプリケーションドメインは通常どおり実行されますが、"" のプロセス "オブジェクトまたは" 表示されない Appdomain "オブジェクトは無効になり、それ以上のコールバックは発生しません。  
  
 .NET Framework バージョン2.0 では、アンマネージデバッグが有効になっている場合、オペレーティングシステムの制限により、このメソッドは失敗します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
