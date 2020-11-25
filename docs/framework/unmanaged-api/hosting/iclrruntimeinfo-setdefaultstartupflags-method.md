---
title: ICLRRuntimeInfo::SetDefaultStartupFlags メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: 8020db491c3b66be38a9f6cbcb7551721859dcd5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723117"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a>ICLRRuntimeInfo::SetDefaultStartupFlags メソッド

ランタイムを開始するために使用されるスタートアップフラグとホスト構成ファイルを設定します。 このメソッドは、 `startupFlags` [Corbindtoruntimeex](corbindtoruntimeex-function.md) および [Corbindtoruntimeex](corbindtoruntimehost-function.md) 関数でのパラメーターの使用よりも優先されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwStartupFlags`  
 から設定するホストスタートアップフラグ。 [Corbindtoruntimeex](corbindtoruntimeex-function.md)および[Corbindtoruntimeex](corbindtoruntimehost-function.md)関数と同じフラグを使用します。  
  
 `pwzHostConfigFile`  
 から設定するホスト構成ファイルのディレクトリパス。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドエラーを示す HRESULT エラーを返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
  
## <a name="remarks"></a>注釈  

 マルチスレッドホストは、このメソッドの呼び出しを同期する必要があります。 それ以外の場合、スレッド B は、の `SetStartupFlags` 呼び出しを完了し `SetStartupFlags` てからランタイムを開始する前に、メソッドを呼び出すことがあります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRRuntimeInfo インターフェイス](iclrruntimeinfo-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
- [ホスティング](index.md)
