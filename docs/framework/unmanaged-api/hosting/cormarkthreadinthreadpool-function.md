---
description: '詳細については、次を参照してください: CorMarkThreadInThreadPool 関数'
title: CorMarkThreadInThreadPool 関数
ms.date: 03/30/2017
api_name:
- CorMarkThreadInThreadPool
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorMarkThreadInThreadPool
helpviewer_keywords:
- CorMarkThreadInThreadPool function [.NET Framework hosting]
ms.assetid: 3f958d41-e82e-4ec3-ae6f-16c7b3b31e3e
topic_type:
- apiref
ms.openlocfilehash: 68d945870075f2f8c06fe76b7a71e2f806078694
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716940"
---
# <a name="cormarkthreadinthreadpool-function"></a>CorMarkThreadInThreadPool 関数

現在実行されているスレッド プールのスレッドに、マネージド コードの実行のマークを付けます。 .NET Framework Version 2.0 以降では、この関数に効力はありません。 必ずしも必要はありませんが、この関数はコードから削除できます。 この関数は .NET Framework 4 では非推奨とされます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
