---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: f0a03ecce49bbc3c1c03d037c9be31a8e994259d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732095"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド

すべてのレガシ共通言語ランタイム (CLR) バージョン2アクティブ化ポリシーの決定に現在のランタイムをバインドします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の Hresult を返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|バインドが成功したか、またはこのランタイムが従来の CLR バージョン2アクティブ化ポリシーのランタイムとして既にバインドされています。|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|以前の CLR バージョン2のアクティブ化ポリシーに、別のランタイムが既にバインドされています。|  
  
## <a name="remarks"></a>注釈  

 現在のランタイムが、従来の CLR バージョン2アクティブ化ポリシーの決定 (構成ファイルの要素で属性を使用するなど) に対して既にバインドされている場合 `useLegacyV2RuntimeActivationPolicy` 、このメソッドはエラー結果を返しません。メソッドが従来のアクティブ化ポリシーに正常にバインドされている場合と同じように、結果が S_OK されます。 [ \<startup> ](../../configure-apps/file-schema/startup/startup-element.md)  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRRuntimeInfo インターフェイス](iclrruntimeinfo-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
- [ホスティング](index.md)
- [\<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)
