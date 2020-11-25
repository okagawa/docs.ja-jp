---
title: EBindPolicyLevels 列挙型
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
ms.openlocfilehash: a0992ca8ac4bfffef681c74de455a0eeb627a042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726848"
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels 列挙型

アセンブリポリシーを適用または変更するレベルを指定するフラグを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|ポリシーを管理者レベルで適用する必要があることを指定します。|  
|`ePolicyLevelApp`|ポリシーをアプリケーションレベルで適用する必要があることを指定します。|  
|`ePolicyLevelHost`|ポリシーをホストレベルで適用する必要があることを指定します。|  
|`ePolicyLevelNone`|ポリシーレベルのフラグを指定しません。|  
|`ePolicyLevelPublisher`|ポリシーをパブリッシャーレベルで適用する必要があることを指定します。|  
|`ePolicyLevelRetargetable`|ポリシーを変数レベルで適用できることを指定します。|  
|`ePolicyPortability`|ポリシーで .NET Framework アセンブリの実装間の移植性をサポートする必要があることを指定します。 構成ファイルの要素を参照してください [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) 。|  
|`ePolicyUnifiedToCLR`|ポリシーを共通言語ランタイム (CLR) のポリシーに統合することを指定します。|  
  
## <a name="remarks"></a>注釈  

 この列挙体は、アプリケーションポリシーの変更を指定するために、 [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) インターフェイスのメソッドに渡されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyIdentityManager インターフェイス](iclrassemblyidentitymanager-interface.md)
- [ホスティングの列挙型](hosting-enumerations.md)
