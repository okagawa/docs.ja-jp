---
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
ms.openlocfilehash: 0c84a91c7da553d0c84a4995b4744576d861dcb9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730202"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint インターフェイス

関数内のブレークポイント、または値のウォッチポイントを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Activate メソッド](icordebugbreakpoint-activate-method.md)|こののアクティブな状態を設定 `ICorDebugBreakpoint` します。|  
|[IsActive メソッド](icordebugbreakpoint-isactive-method.md)|このがアクティブかどうかを示す値を取得し `ICorDebugBreakpoint` ます。|  
  
## <a name="remarks"></a>注釈  

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
