---
description: 詳細については、「ICorDebugBreakpoint インターフェイス」を参照してください。
title: ICorDebugBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 63917512cceeccedea37acdf2ba7ab3b849d9fad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711805"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint インターフェイス

関数内のブレークポイント、または値のウォッチポイントを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Activate メソッド](icordebugbreakpoint-activate-method.md)|こののアクティブな状態を設定 `ICorDebugBreakpoint` します。|  
|[IsActive メソッド](icordebugbreakpoint-isactive-method.md)|このがアクティブかどうかを示す値を取得し `ICorDebugBreakpoint` ます。|  
  
## <a name="remarks"></a>解説  

 ブレークポイントは、条件式を直接サポートしません。 このような機能が必要な場合は、デバッガーでを上に実装する必要があり `ICorDebugBreakpoint` ます。  
  
 は、 `ICorDebugBreakpoint` 関数内のブレークポイントをサポートするために、によって拡張されます。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
