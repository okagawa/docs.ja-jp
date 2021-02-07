---
description: '詳細については、次のページを参照してください: を参照'
title: ICorDebugExceptionDebugEvent::GetFlags メソッド
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 54a6c9b0dff2346ca130f80e72fe06dbb3017f10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693474"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a>ICorDebugExceptionDebugEvent::GetFlags メソッド

例外をインターセプトできるかどうかを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pdwFlags`  
 入出力例外をインターセプトできるかどうかを示す [Cordebugexceptionflags](cordebugexceptionflags-enumeration.md) 値へのポインター。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugExceptionDebugEvent インターフェイス](icordebugexceptiondebugevent-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
