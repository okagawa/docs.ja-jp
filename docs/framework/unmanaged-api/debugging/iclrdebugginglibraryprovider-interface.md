---
title: ICLRDebuggingLibraryProvider インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
ms.openlocfilehash: cd17cbc808b7f8381ac320bb55999c6b0466c3d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723539"
---
# <a name="iclrdebugginglibraryprovider-interface"></a>ICLRDebuggingLibraryProvider インターフェイス

には、提供 [ライブラリのメソッド](iclrdebugginglibraryprovider-providelibrary-method.md) メソッドが含まれています。このメソッドは、共通言語ランタイムのバージョン固有のデバッグライブラリをオンデマンドで検索して読み込むことができるようにする、ライブラリプロバイダーのコールバックインターフェイスを取得します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ProvideLibrary メソッド](iclrdebugginglibraryprovider-providelibrary-method.md)|デバッガーが、デバッグライブラリの読み込みに使用できるモジュールへのハンドルを提供できるようにします。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
