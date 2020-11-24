---
title: ICorPublishProcess::EnumAppDomains メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: 2acf8fb507ab617e066a31c9c2657b1ef0d18e47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693282"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains メソッド

この [ICorPublishProcess](icorpublishprocess-interface.md)によって参照されるプロセス内のアプリケーションドメインの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppEnum`  
 入出力このプロセス内のアプリケーションドメインのコレクションを反復処理できる [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) インスタンスのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 アプリケーションドメインの一覧は、メソッドが呼び出されたときに存在するアプリケーションドメインのスナップショットに基づいてい `EnumAppDomains` ます。 このメソッドは、新しい最新の一覧を作成するために複数回呼び出すことができます。 既存のリストは、このメソッドの後続の呼び出しの影響を受けません。  
  
 プロセスが終了した場合、 `EnumAppDomains` は CORDBG_E_PROCESS_TERMINATED の HRESULT 値で失敗します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublishProcess インターフェイス](icorpublishprocess-interface.md)
