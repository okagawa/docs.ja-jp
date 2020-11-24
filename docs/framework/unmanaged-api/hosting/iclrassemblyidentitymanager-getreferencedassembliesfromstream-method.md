---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
ms.openlocfilehash: a5e71d6ca90c8d0aa489176eb5a90bfe6896b1cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679322"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a>ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド

指定したストリーム内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納する [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) オブジェクトへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pStream`  
 から `IStream` 評価されるアセンブリを格納しているへのインターフェイスポインター。  
  
 `dwFlags`  
 から将来の拡張のために提供されます。 CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンでサポートされている唯一の値です。  
  
 `pExcludeAssembliesList`  
 から除外されるアセンブリのアセンブリ id データを格納する [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) オブジェクトへのポインター `ppReferenceEnum` 。  
  
 `ppReferenceEnum`  
 入出力内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納するオブジェクトのアドレスへのポインター `ICLRReferenceAssemblyEnum` `pStream` (内のアセンブリは除く) `pExcludeAssembliesList` 。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドから正常に値が返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>注釈  

 呼び出し元は、返された一覧から一連の既知のアセンブリ参照を除外することを選択できます。 このセットはによって定義され `pExcludeAssembliesList` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyIdentityManager インターフェイス](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList インターフェイス](iclrassemblyreferencelist-interface.md)
- [ICLRReferenceAssemblyEnum インターフェイス](iclrreferenceassemblyenum-interface.md)
