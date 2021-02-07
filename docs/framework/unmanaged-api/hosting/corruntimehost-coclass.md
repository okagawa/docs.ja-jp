---
description: '詳細については、次を参照してください: CorRuntimeHost コクラス'
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
ms.openlocfilehash: cd2d01075e5c8264337e1e989b3d9fdc6bf68962
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760642"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost コクラス

共通言語ランタイムによって実行されるアプリケーションを管理するためのインターフェイスを提供します。  
  
## <a name="syntax"></a>構文  
  
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
