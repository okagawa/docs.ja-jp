---
description: '詳細について: ICLRTask2:: BeginPreventAsyncAbort メソッド'
title: ICLRTask2::BeginPreventAsyncAbort メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: 1e25cb0e6157d77efc6a04016dc49d9d5d0bf116
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728634"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a>ICLRTask2::BeginPreventAsyncAbort メソッド

現在のスレッドでのスレッドの中止要求から、新しいスレッド中止要求を遅延します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|HOST_E_INVALIDOPERATION|メソッドは、現在のスレッドではないスレッドで呼び出されました。|  
  
## <a name="remarks"></a>解説  

 このメソッドを呼び出すと、現在のスレッドの遅延スレッド中止カウンターが1つ増加します。  
  
 `BeginPreventAsyncAbort`と[ICLRTask2:: EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md)の呼び出しは入れ子にすることができます。 カウンターがゼロより大きい限り、現在のスレッドのスレッド中止は遅延されます。 この呼び出しがメソッドの呼び出しとペアリングされていない場合 `EndPreventAsyncAbort` 、スレッドの中止が現在のスレッドに配信されない状態になる可能性があります。  
  
 遅延は、それ自体を中止するスレッドには適用されません。  
  
 この機能によって公開されている機能は、仮想マシン (VM) によって内部的に使用されます。 これらの方法を誤用すると、VM で特定できない動作が発生する可能性があります。 たとえば、最初に `EndPreventAsyncAbort` を呼び出しないでを呼び出す `BeginPreventAsyncAbort` と、VM で以前にインクリメントしたカウンターが0に設定されます。 同様に、内部カウンターのオーバーフローはチェックされません。 ホストと VM の両方によってインクリメントされるために整数の制限を超えた場合、結果として得られる動作は指定されません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EndPreventAsyncAbort メソッド](iclrtask2-endpreventasyncabort-method.md)
- [ICLRTask2 インターフェイス](iclrtask2-interface.md)
- [ICLRTaskManager インターフェイス](iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](ihosttask-interface.md)
- [IHostTaskManager インターフェイス](ihosttaskmanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
