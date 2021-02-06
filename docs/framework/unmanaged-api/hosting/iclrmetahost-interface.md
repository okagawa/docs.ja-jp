---
description: 詳細については、「ICLRMetaHost インターフェイス」を参照してください。
title: ICLRMetaHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 5dc50af85c067bcb525414e47cddd34070b83a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637509"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost インターフェイス

バージョン番号に基づいて特定のバージョンの共通言語ランタイム (CLR) を返すメソッド、インストールされているすべての CLRs の一覧表示、指定されたプロセスに読み込まれたすべてのランタイムの一覧表示、アセンブリをコンパイルするために使用される CLR バージョンの検出、クリーンランタイムシャットダウンを使用したプロセスの終了、従来の API バインディングのクエリを  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes メソッド](iclrmetahost-enumerateinstalledruntimes-method.md)|コンピューターにインストールされている各 CLR バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙を返します。|  
|[EnumerateLoadedRuntimes メソッド](iclrmetahost-enumerateloadedruntimes-method.md)|指定されたプロセスに読み込まれる各 CLR の有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙体を返します。 このメソッドは、 [Getversionfromprocess](getversionfromprocess-function.md)よりも優先します。|  
|[ExitProcess メソッド](iclrmetahost-exitprocess-method.md)|読み込まれたすべてのランタイムを正常にシャットダウンしてから、プロセスを終了しようとします。 [CorExitProcess](corexitprocess-function.md)関数よりも優先されます。|  
|[GetRuntime メソッド](iclrmetahost-getruntime-method.md)|特定の CLR バージョンに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを取得します。 このメソッドは、 [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)フラグと共に使用される[Corbindtoruntimeex](corbindtoruntimeex-function.md)関数よりも優先されます。|  
|[GetVersionFromFile メソッド](iclrmetahost-getversionfromfile-method.md)|ファイルパスを指定して、アセンブリの元の .NET Framework コンパイルバージョン (メタデータに格納されている) を取得します。 このメソッドは、 [GetFileVersion](getfileversion-function.md)よりも優先します。|  
|[QueryLegacyV2RuntimeBinding メソッド](iclrmetahost-querylegacyv2runtimebinding-method.md)|レガシアクティブ化ポリシーがバインドされているランタイムを表すインターフェイスを返します。たとえば、 `useLegacyV2RuntimeActivationPolicy` [ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)構成ファイルのエントリで属性を使用したり、レガシアクティベーション api を直接使用したり、 [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッドを呼び出したりします。|  
|[RequestRuntimeLoadedNotification メソッド](iclrmetahost-requestruntimeloadednotification-method.md)|CLR バージョンが最初に読み込まれたが、まだ開始されていない場合は、指定された関数ポインターへのコールバックを保証します。 このメソッドは、 [Lockclrversion](lockclrversion-function.md)を置き換えます。|  
  
## <a name="remarks"></a>解説  

 このインターフェイスのインスタンスを取得する唯一の方法は、 [Clrcreateinstance](clrcreateinstance-function.md) 関数を次のように呼び出します。  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](hosting-interfaces.md)
- [ホスティング](index.md)
