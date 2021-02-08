---
description: 詳細については、「ICorPublishProcessEnum インターフェイス」を参照してください。
title: ICorPublishProcessEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 87d80d066995dbeca67f461e01652dd3deb3bf1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790491"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum インターフェイス

[ICorPublishProcess](icorpublishprocess-interface.md)オブジェクトのコレクションを走査するメソッドを提供する[ICorPublishEnum](icorpublishenum-interface.md)インターフェイスのサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[次のメソッド](icorpublishprocessenum-next-method.md)|現在の位置から開始して、指定した数の `ICorPublishProcess` インスタンスをコレクションから取得します。|  
  
## <a name="remarks"></a>解説  

 インターフェイスは、 `ICorPublishProcessEnum` 抽象インターフェイス [ICorPublishEnum](icorpublishenum-interface.md)のメソッドを実装します。  
  
 `ICorPublishProcessEnum`インスタンスは、 [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md)メソッドによって作成されます。 オブジェクトのコレクションの走査 `ICorPublishProcess` は、インスタンスの作成時に指定されたフィルター条件に基づいてい `ICorPublishProcessEnum` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [CorpubPublish コクラス](corpubpublish-coclass.md)
