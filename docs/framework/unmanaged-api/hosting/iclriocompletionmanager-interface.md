---
description: '詳細情報: Iclrio参照マネージャーインターフェイス'
title: ICLRIoCompletionManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: b2d18f9c9900d448f0c6517520c303eb4258f8d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789889"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager インターフェイス

ホストが、指定された i/o 要求のステータスの共通言語ランタイム (CLR) に通知するためのコールバックメソッドを実装します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[OnComplete メソッド](iclriocompletionmanager-oncomplete-method.md)|[Ihohooの](ihostiocompletionmanager-bind-method.md)呼び出しを使用して作成された i/o 要求の状態を CLR に通知します:: Bind メソッド。|  
  
## <a name="remarks"></a>解説  

 ホストは、 [Ihohoocompletion manager](ihostiocompletionmanager-interface.md) インターフェイスを使用して i/o 完了の抽象化を実装します。 CLR はこのインターフェイスを介して i/o 要求を行い、ホストはインターフェイスを使用して、そのような要求の結果をランタイムに通知し `ICLRIoCompletionManager` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostIoCompletionManager インターフェイス](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager インターフェイス](ihostthreadpoolmanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
