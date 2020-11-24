---
title: ICorPublishEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: 492d4b727ce507340fec47d30a791aa49d0cecb6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693347"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum インターフェイス

プロセスおよびアプリケーションドメインに関する情報の公開に使用される列挙子の抽象基本インターフェイスとして機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](icorpublishenum-clone-method.md)|この `ICorPublishEnum` オブジェクトのコピーを作成します。|  
|[GetCount メソッド](icorpublishenum-getcount-method.md)|列挙に含まれる項目の数を取得します。|  
|[Reset メソッド](icorpublishenum-reset-method.md)|のカーソルを列挙体の先頭に移動します。|  
|[Skip メソッド](icorpublishenum-skip-method.md)|指定した数の項目だけ、列挙内でカーソルを前方に移動します。|  
  
## <a name="remarks"></a>注釈  

 次の列挙子は、から派生し `ICorPublishEnum` ます。  
  
- [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CorpubPublish コクラス](corpubpublish-coclass.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
