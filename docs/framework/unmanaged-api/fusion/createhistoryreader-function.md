---
description: '詳細情報: Createhistory Reader 関数'
title: CreateHistoryReader 関数
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
ms.openlocfilehash: 0943f3d0f3322d34ed92c0a96b909e4d63ec5e7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761123"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader 関数

指定されたファイルの履歴リーダーを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>パラメーター  

 `wzFilePath`  
 からファイルパス。  
  
 `ppHistoryReader`  
 入出力正常に完了した場合は、履歴リーダーへのポインターが含まれます。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の表で説明する値に加えて、Winerror.h で定義されている標準 COM エラーコードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドが正常に完了したことを示します。|  
|E_INVALIDARG|`wzFilePath`または `ppHistoryReader` が null 参照に設定されていることを示します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ライブラリ:** Fusion.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion グローバル静的関数](fusion-global-static-functions.md)
