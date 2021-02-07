---
description: '詳細情報: GetHistoryFileDirectory 関数'
title: GetHistoryFileDirectory 関数
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
ms.openlocfilehash: 960bc75d69f4be6d1639e109d6327b5e65d3e129
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760967"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory 関数

アプリケーション履歴ディレクトリのパスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wzDir`  
 入出力アプリケーション履歴ディレクトリへのパスを保持するバッファー。  
  
 `pdwSize`  
 [入力、出力]バッファーの長さ。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、Winerror.h ファイルで定義されているように、次の値に加えて、標準の COM エラーコードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`wzDir` または `pdwSize` が null であるか、またはバージョン文字列が正しくありません。|  
  
## <a name="remarks"></a>解説  

 正常に完了すると、 `pdwSize` 引数はパス文字列の長さに設定されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **Library:** Fusion.dll し、Mscorwks.dll します。 Mscorwks.dll ではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にするようにします。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CreateHistoryReader 関数](createhistoryreader-function.md)
- [NukeDownloadedCache 関数](nukedownloadedcache-function.md)
- [Fusion グローバル静的関数](fusion-global-static-functions.md)
