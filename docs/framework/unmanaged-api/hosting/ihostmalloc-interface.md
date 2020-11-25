---
title: IHostMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: 2530c7fcd63f81b566d6623a533bd8e2af084047
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702161"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc インターフェイス

共通言語ランタイム (CLR) がホストを介してヒープから細かい割り当てを要求できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Alloc メソッド](ihostmalloc-alloc-method.md)|ホストがヒープから要求された量のメモリを割り当てることを要求します。|  
|[DebugAlloc メソッド](ihostmalloc-debugalloc-method.md)|は、要求されたメモリ量をヒープから割り当て、さらにメモリが割り当てられた場所を追跡することをホストに要求します。|  
|[Free メソッド](ihostmalloc-free-method.md)|メソッドを使用して割り当てられたメモリを解放し `Alloc` ます。|  
  
## <a name="remarks"></a>注釈  

 CLR は、 `IHostMalloc` [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) メソッドを呼び出すことによって、インスタンスへのインターフェイスポインターを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostMemoryManager インターフェイス](ihostmemorymanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
