---
description: '詳細については、次の情報を参照してください: の値インターフェイス'
title: ICorDebugObjectValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: a2af438bbb4c2f56eb1a72151e339b6b0a978eec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794772"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue インターフェイス

オブジェクトを含む値を表す "ICorDebugValue" のサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetClass メソッド](icordebugobjectvalue-getclass-method.md)|<xref:System.Type>このが参照するオブジェクトの共通言語ランタイム (CLR) へのインターフェイスポインターを取得し `ICorDebugObjectValue` ます。|  
|[GetContext メソッド](icordebugobjectvalue-getcontext-method.md)|実装されていません。|  
|[GetFieldValue メソッド](icordebugobjectvalue-getfieldvalue-method.md)|指定したクラスの指定したフィールドの値を表す、 [ICorDebugValue](icordebugvalue-interface.md) へのインターフェイスポインターを取得します。|  
|[GetManagedCopy メソッド](icordebugobjectvalue-getmanagedcopy-method.md)|互換性のために残されています。 このメソッドは呼び出さないでください。|  
|[GetVirtualMethod メソッド](icordebugobjectvalue-getvirtualmethod-method.md)|実装されていません。|  
|[IsValueClass メソッド](icordebugobjectvalue-isvalueclass-method.md)|このによって参照されるオブジェクトが値型かどうかを示す値を取得し `ICorDebugObjectValue` ます。|  
|[SetFromManagedCopy メソッド](icordebugobjectvalue-setfrommanagedcopy-method.md)|互換性のために残されています。 このメソッドは呼び出さないでください。|  
  
## <a name="remarks"></a>解説  

 は、 `ICorDebugObjectValue` デバッグ中のプロセスが続行されるまで有効なままです。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
