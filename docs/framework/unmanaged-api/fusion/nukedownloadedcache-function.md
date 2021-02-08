---
description: '詳細情報: NukeDownloadedCache 関数'
title: NukeDownloadedCache 関数
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
ms.openlocfilehash: 2239473b8e6e43a539b0507c8255d40f87e72043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800033"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache 関数

共通言語ランタイム (CLR) のダウンロードキャッシュを削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、Winerror.h で定義されているように、標準の COM エラーコードを返します。  
  
## <a name="remarks"></a>解説  

 CLR ダウンロードキャッシュは、URL からダウンロードされる厳密な名前付きアセンブリが再利用できるように格納される領域です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **Library:** Fusion.dll し、Mscorwks.dll します。 Mscorwks.dll ではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にするようにします。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CreateHistoryReader 関数](createhistoryreader-function.md)
- [GetHistoryFileDirectory 関数](gethistoryfiledirectory-function.md)
- [Fusion グローバル静的関数](fusion-global-static-functions.md)
