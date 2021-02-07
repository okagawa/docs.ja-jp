---
description: 詳細については、「ICorDebugAppDomain2 インターフェイス」を参照してください。
title: ICorDebugAppDomain2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: 2f2fcc4166a0c825abaa04392f9905d17e286803
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754187"
---
# <a name="icordebugappdomain2-interface"></a>ICorDebugAppDomain2 インターフェイス

配列、ポインター、関数ポインター、および参照型を操作するメソッドを提供します。 このインターフェイスは、の機能を持つ Appdomain インターフェイスの拡張です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetArrayOrPointerType メソッド](icordebugappdomain2-getarrayorpointertype-method.md)|指定した型、または指定した型へのポインターまたは参照の配列を取得します。|  
|[GetFunctionPointerType](icordebugappdomain2-getfunctionpointertype-method.md)|指定されたシグネチャを持つ関数へのポインターを取得します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
