---
title: AssemblyBindInfo 構造体
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: d2ba7d8e66472f771a932a2dfb05bb9e1ee96290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685878"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo 構造体

参照アセンブリに関する詳細情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dwAppDomainId`|`IStream` [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md)への呼び出しによって返されるの一意の識別子。参照されるアセンブリが読み込まれます。|  
|`lpReferencedIdentity`|参照アセンブリの一意の識別子。|  
|`lpPostPolicyIdentity`|バインドポリシー値の適用後に参照されるアセンブリの識別子。|  
|`ePolicyLevel`|参照先のアセンブリに適用するバージョン管理ポリシーを示す [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。|  
  
## <a name="remarks"></a>注釈  

 ホストは、一意の識別子 `dwAppDomainId` を共通言語ランタイム (CLR) に提供します。 の呼び出しが戻ると、 `IHostAssemblyStore::ProvideAssembly` ランタイムは識別子を使用して、の内容が `IStream` マップされているかどうかを判断します。 その場合、ランタイムはストリームを再マップするのではなく、既存のコピーを読み込みます。 ランタイムは、 [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md)への呼び出しから返されたストリームの参照キーとしても、この識別子を使用します。 このため、識別子はモジュール要求とアセンブリ要求に対して一意である必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](hosting-structures.md)
- [ICLRAssemblyIdentityManager インターフェイス](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList インターフェイス](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager インターフェイス](ihostassemblymanager-interface.md)
- [IHostAssemblyStore インターフェイス](ihostassemblystore-interface.md)
- [ModuleBindInfo 構造体](modulebindinfo-structure.md)
