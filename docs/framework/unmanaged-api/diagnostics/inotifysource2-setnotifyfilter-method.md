---
description: '詳細について: INotifySource2:: SetNotifyFilter メソッド'
title: INotifySource2::SetNotifyFilter メソッド
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 2aaf2a5253f8a9acb67c4b538f109a7a62559d12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800228"
---
# <a name="inotifysource2setnotifyfilter-method"></a>INotifySource2::SetNotifyFilter メソッド

このソースで使用する通知フィルターを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `in_NotifyFilter`  
 からデバッガー API のコールバックを識別する [NOTIFY_FILTER](notify-filter-enumeration.md) 列挙値のビットごとの組み合わせ。  
  
 `in_pUserThreadFilter`  
 からデバッガー API のスレッドを識別する [USER_THREAD](user-thread-structure.md) 構造体へのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** ProtocolNotify2  
  
## <a name="see-also"></a>関連項目

- [INotifySource2 インターフェイス](inotifysource2-interface.md)
- [INotifyConnection2 インターフェイス](inotifyconnection2-interface.md)
- [INotifySink2 インターフェイス](inotifysink2-interface.md)
