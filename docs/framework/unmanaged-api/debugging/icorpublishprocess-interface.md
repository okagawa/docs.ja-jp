---
title: ICorPublishProcess インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 8ee59e9d416d1c53312e4fccb6953f20b03b29b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693087"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess インターフェイス

プロセスについて表示される情報にアクセスするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumAppDomains メソッド](icorpublishprocess-enumappdomains-method.md)|このによって参照されるプロセス内のアプリケーションドメインを格納している [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) インスタンスを取得し `ICorPublishProcess` ます。|  
|[GetDisplayName メソッド](icorpublishprocess-getdisplayname-method.md)|このによって参照されるプロセスの実行可能ファイルの完全パスを取得し `ICorPublishProcess` ます。|  
|[GetProcessID メソッド](icorpublishprocess-getprocessid-method.md)|このによって参照されるプロセスのオペレーティングシステム識別子を取得し `ICorPublishProcess` ます。|  
|[IsManaged メソッド](icorpublishprocess-ismanaged-method.md)|このによって参照されるプロセス `ICorPublishProcess` がマネージコードを実行していることがわかっているかどうかを示す値を取得します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [CorpubPublish コクラス](corpubpublish-coclass.md)
