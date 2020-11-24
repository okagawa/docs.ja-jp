---
title: CorRuntimeHost コクラス
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: cd4e675b4ba50b47146428d204c28cc943c23c69
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688004"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost コクラス

共通言語ランタイムによって実行されるアプリケーションを管理するためのインターフェイスを提供します。  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>インターフェイス  
  
|インターフェイス|説明|  
|---------------|-----------------|  
|[ICorConfiguration インターフェイス](icorconfiguration-interface.md)|共通言語ランタイム (CLR: common language runtime) を構成するためのメソッドを提供します。|  
|[ICorRuntimeHost インターフェイス](icorruntimehost-interface.md)|ホストが共通言語ランタイムを明示的に開始または停止したり、アプリケーションドメインを作成および構成したり、既定のドメインにアクセスしたり、プロセスで実行されているすべてのドメインを列挙したりできるようにするメソッドを提供します。|  
|[IDebuggerInfo Iインターフェイス](idebuggerinfo-interface.md)|デバッグサービスの状態に関する情報を取得するためのメソッドを提供します。|  
|[IGCHost インターフェイス](igchost-interface.md)|ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。|  
|IValidator|ポータブル実行可能イメージを検証し、検証エラーの詳細なレポートを作成するためのメソッドを提供します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト コクラス](hosting-coclasses.md)
