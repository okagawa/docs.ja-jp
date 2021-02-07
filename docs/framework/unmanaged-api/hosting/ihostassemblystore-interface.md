---
description: 詳細については、「IHostAssemblyStore インターフェイス」を参照してください。
title: IHostAssemblyStore インターフェイス
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: a05fee7916911687143d5953e26187162a2fa544
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709036"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore インターフェイス

共通言語ランタイム (CLR) とは独立して、ホストがアセンブリとモジュールを読み込むことができるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ProvideAssembly メソッド](ihostassemblystore-provideassembly-method.md)|[IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)の呼び出しから返された[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)によって参照されていないアセンブリへの参照を取得します。|  
|[ProvideModule メソッド](ihostassemblystore-providemodule-method.md)|アセンブリ内のモジュール、またはリンクされた (埋め込まれていない) リソースファイル内のモジュールを解決します。|  
  
## <a name="remarks"></a>解説  

 `IHostAssemblyStore` ホストがアセンブリ id に基づいてアセンブリを効率的に読み込む方法を提供します。 ホストは、 `IStream` バイトを直接指し示すインスタンスを返すことによって、アセンブリを読み込みます。  
  
 CLR は、 `IHostAssemblyStore` 初期化時にを呼び出すことによってホストが実装されているかどうかを判断し `IHostAssemblyManager::GetNonHostAssemblyStores` ます。 これにより、ホストは、たとえば、ユーザーアセンブリへのバインドを制御できますが、ランタイムに依存して .NET Framework アセンブリにバインドすることができます。  
  
> [!NOTE]
> の実装を提供 `IHostAssemblyStore` する場合、ホストはから返されたによって参照されていないすべてのアセンブリを解決するための目的を指定し `ICLRAssemblyReferenceList` `IHostAssemblyManager::GetNonHostStoreAssemblies` ます。  
  
> [!NOTE]
> .NET Framework バージョン2.0 では、 [ネイティブイメージジェネレーター (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) ユーティリティによって提供されるように、アセンブリのネイティブイメージをホストが読み込むことはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyReferenceList インターフェイス](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager インターフェイス](ihostassemblymanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
