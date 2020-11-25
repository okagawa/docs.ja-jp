---
title: CorpubPublish コクラス
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: c73eab14bf6f9f9599bed79f4c5f85ed035c0518
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722350"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish コクラス

アプリケーション ドメインとプロセスに関する情報を発行するためのインターフェイスを提供します。  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>インターフェイス  
  
|インターフェイス|説明|  
|---------------|-----------------|  
|[ICorPublish インターフェイス](icorpublish-interface.md)|プロセスおよびプロセス内のアプリケーションドメインに関する情報を公開するためのメソッドを提供します。|  
|[ICorPublishAppDomain インターフェイス](icorpublishappdomain-interface.md)|プロセス内のアプリケーションドメインに関する情報を表し、提供します。|  
|[ICorPublishAppDomainEnum インターフェイス](icorpublishappdomainenum-interface.md)|プロセス内に現在存在するアプリケーションドメインのコレクションを走査するメソッドを提供します。|  
|[ICorPublishProcess インターフェイス](icorpublishprocess-interface.md)|コンピューター上で実行されているプロセスを表します。|  
|[ICorPublishProcessEnum インターフェイス](icorpublishprocessenum-interface.md)|コンピューター上で実行されているプロセスのコレクションを走査するメソッドを提供します。|  
  
## <a name="remarks"></a>注釈  

 一般的な発行シナリオでは、開発者がアプリケーションドメイン内のコンピューターで実行されているマネージコードをデバッグする必要があります。 ホスト環境で、プロセス内で複数のアプリケーションドメインが実行されている可能性があります。 開発者は、コンピューター上で実行されているすべてのプロセスを一覧表示し、特定のプロセスを選択するために、グラフィカルユーザーインターフェイスまたはその他の方法を使用したいと考えています。 この一覧には、マネージコードを実行しているプロセス内のすべてのアプリケーションドメインが含まれている必要があります。 開発者は、特定のアプリケーションドメインを特定し、そのドメインにデバッガーをアタッチできます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
