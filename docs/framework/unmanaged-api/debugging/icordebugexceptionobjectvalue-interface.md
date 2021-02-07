---
description: '詳細については、次の情報を参照してください。: の値インターフェイス'
title: ICorDebugExceptionObjectValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
ms.openlocfilehash: 67672f9921bab31019a42b742480176e6d0bf3d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693201"
---
# <a name="icordebugexceptionobjectvalue-interface"></a>ICorDebugExceptionObjectValue インターフェイス

"は、マネージ例外オブジェクトからスタックトレース情報を提供するために、" は、"" のような "のインターフェイスを拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateExceptionCallStack メソッド](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|例外オブジェクトに埋め込まれている呼び出し履歴に対する列挙子を取得します。|  
  
## <a name="remarks"></a>解説  

 の呼び出しは、 `QueryInterface` から派生したマネージオブジェクトに対して成功し <xref:System.Exception?displayProperty=nameWithType> ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
