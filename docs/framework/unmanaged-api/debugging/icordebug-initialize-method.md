---
description: '詳細情報: ICorDebug:: Initialize メソッド'
title: ICorDebug::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: 6b6ddd8c1c21470477420909bcf75906b5731ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791596"
---
# <a name="icordebuginitialize-method"></a>ICorDebug::Initialize メソッド

`ICorDebug` オブジェクトを初期化します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a>解説  

 デバッガーは、 `Initialize` 作成時にを呼び出して、デバッグサービスを初期化する必要があります。 このメソッドは、の他のメソッドが呼び出される前に呼び出す必要があり `ICorDebug` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
