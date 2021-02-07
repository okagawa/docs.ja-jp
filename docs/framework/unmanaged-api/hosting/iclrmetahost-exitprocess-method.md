---
description: '詳細について: ICLRMetaHost:: ExitProcess メソッド'
title: ICLRMetaHost::ExitProcess メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 3bc832538a5ad2b457de758fc35a632b09c02974
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689158"
---
# <a name="iclrmetahostexitprocess-method"></a>ICLRMetaHost::ExitProcess メソッド

読み込まれたすべてのランタイムを正常にシャットダウンしてから、プロセスを終了しようとします。 [CorExitProcess](corexitprocess-function.md)関数よりも優先されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a>パラメーター  

 `iExitCode`  
 からプロセスの終了コード。  
  
## <a name="return-value"></a>戻り値  

 このメソッドはを返しません。そのため、戻り値は未定義です。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMetaHost インターフェイス](iclrmetahost-interface.md)
- [ホスティング](index.md)
