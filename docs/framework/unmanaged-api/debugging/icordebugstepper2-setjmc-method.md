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
ms.openlocfilehash: ab1351af042aba5042cc7a04614bc3cf14f7d7ae
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379462"
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
 から`true`アプリケーションの開発者によって作成されたコードのみをステップ実行するには、をに設定します。それ以外の場合はに設定 `false` します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
