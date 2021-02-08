---
description: '詳細について: ICLRMetaHost:: EnumerateLoadedRuntimes メソッド'
title: ICLRMetaHost::EnumerateLoadedRuntimes メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 508c4daca7e34366e0da35591f4e7a780301e823
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789867"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a>ICLRMetaHost::EnumerateLoadedRuntimes メソッド

指定されたプロセスに読み込まれる共通言語ランタイム (CLR) の各バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙体を返します。 このメソッドは、 [Getversionfromprocess](getversionfromprocess-function.md) 関数よりも優先されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `hndProcess`  
 から読み込まれたランタイムを検査するプロセスのハンドル。  
  
 `ppEnumerator`  
 入出力 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> プロセスによって読み込まれる各 CLR に対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスの列挙体。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`ppEnumerator` が null です。|  
  
## <a name="remarks"></a>解説  

 このメソッドは、 [Corbindtoruntime](corbindtoruntime-function.md)などの非推奨の関数を使用して読み込まれた場合でも、読み込まれたすべてのランタイムを一覧表示します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMetaHost インターフェイス](iclrmetahost-interface.md)
- [ホスティング](index.md)
