---
title: ICLRErrorReportingManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
ms.openlocfilehash: d3816c8a3b6204b053505aa888eb28d696f8990b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677846"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager インターフェイス

エラー報告のためにホストがカスタムスタックダンプを構成できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BeginCustomDump メソッド](iclrerrorreportingmanager-begincustomdump-method.md)|エラー報告用のカスタムスタックダンプの構成を指定します。|  
|[EndCustomDump メソッド](iclrerrorreportingmanager-endcustomdump-method.md)|以前のの呼び出しで設定されたカスタムスタックダンプ構成を消去し `BeginCustomDump` ます。|  
|[GetBucketParametersForCurrentException メソッド](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|呼び出し元のスレッドで現在の例外の Watson バケットを取得します。|  
  
## <a name="remarks"></a>注釈  

 メソッドは、 `BeginCustomDump` カスタムスタックダンプ構成を設定します。 メソッドは、 `EndCustomDump` カスタムスタックダンプ構成をクリアし、関連付けられているすべての状態を解放します。 カスタムダンプの完了後に呼び出す必要があります。  
  
> [!IMPORTANT]
> を呼び出さない `EndCustomDump` と、メモリがリークします。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ECustomDumpItemKind 列挙型](ecustomdumpitemkind-enumeration.md)
- [ホスト インターフェイス](hosting-interfaces.md)
