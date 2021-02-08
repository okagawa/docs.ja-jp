---
description: 詳細については、「ICorPublishProcess インターフェイス」を参照してください。
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
ms.openlocfilehash: 8dbc619d33c2c9b625dde852948dff00b5be926e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800878"
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
