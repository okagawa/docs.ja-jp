---
description: '詳細について: ICLRMetaHost:: QueryLegacyV2RuntimeBinding メソッド'
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: ae825c2b2dfe2ce5b75ac9b82511215704fa357f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789854"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding メソッド

レガシアクティブ化ポリシーがバインドされているランタイムを表すインターフェイスを返します。たとえば、 `useLegacyV2RuntimeActivationPolicy` [ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)構成ファイルのエントリで属性を使用するか、レガシアクティベーション api を直接使用するか、 [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>パラメーター  

 `riid`  
 から必須。現時点では、このパラメーターの有効な `IID_ICLRRuntimeInfo` 値はのみです。  
  
 `ppUnk`  
 [out] 必須。 このメソッドから制御が戻るときに、レガシアクティブ化ポリシーにバインドされているランタイムを表す [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスへのポインターを格納します。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了し、レガシ アクティブ化ポリシーにバインドされているランタイムが返されました。|  
|S_FALSE|メソッドは正常に完了しましたが、レガシ ランタイムはまだバインドされていません。|  
|E_NOINTERFACE|メソッドで、レガシ アクティブ化ポリシーにバインドされているランタイムが見つかりましたが、`riid` はそのランタイムでサポートされていません。|  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMetaHost インターフェイス](iclrmetahost-interface.md)
- [ホスティング](index.md)
