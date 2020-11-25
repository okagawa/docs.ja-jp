---
title: ICorDebugStepper2::SetJMC メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
ms.openlocfilehash: 1bbcbcfbb78d421f247a13f58070b68f701e4ed1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697208"
---
# <a name="icordebugstepper2setjmc-method"></a>ICorDebugStepper2::SetJMC メソッド

この ICorDebugStepper が、アプリケーションの開発者によって作成されたコードのみを使用するかどうかを指定する値を設定します。 このプロセスは、"マイコードのみ" (JMC) デバッグとも呼ばれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `fIsJMCStepper`  
 から `true` アプリケーションの開発者によって作成されたコードのみをステップ実行するには、をに設定します。それ以外の場合はに設定 `false` します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
