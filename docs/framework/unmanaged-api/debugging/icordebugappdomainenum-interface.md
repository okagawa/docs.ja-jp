---
title: ICorDebugAppDomainEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: 37b6bcb48681704e3db47f81a51a9d21f00dfb37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723195"
---
# <a name="icordebugappdomainenum-interface"></a>ICorDebugAppDomainEnum インターフェイス

`Next`列挙体の次の位置から始まる指定された数の値を返すメソッドを提供し `ICorDebugAppDomainEnum` ます。 このインターフェイスは、"ICorDebugEnum" のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Next メソッド](icordebugappdomainenum-next-method.md)|現在のカーソル位置から開始して、指定した数のアプリケーションドメインをコレクションから取得します。|  
  
## <a name="remarks"></a>注釈  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
