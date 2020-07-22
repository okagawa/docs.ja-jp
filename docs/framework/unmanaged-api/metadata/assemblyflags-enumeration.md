---
title: AssemblyFlags 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 1cb84b94b37a2e9e8dd4d20d09cbca82db290c0f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009454"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags 列挙体
アセンブリのランタイム機能を記述する値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`afImplicitExportedTypes`|エクスポートされた型定義が、アセンブリを構成するファイル内で暗黙的に指定されることを指定します。 .NET Framework バージョン1.0 および1.1 では、この値は常に設定されると想定されます。|  
|`afImplicitResources`|アセンブリを構成するファイル内でリソース定義が暗黙的であることを指定します。 .NET Framework 1.0 および1.1 では、この値は常に設定されると想定されます。|  
|`afNonSideBySideAppDomain`|アセンブリが同じアプリケーションドメインで実行されている場合、その他のバージョンでは実行できないことを指定します。|  
|`afNonSideBySideProcess`|同じプロセスで実行されている場合、アセンブリを他のバージョンと一緒に実行できないことを指定します。|  
|`afNonSideBySideMachine`|アセンブリが同じコンピューター上で実行されている場合、その他のバージョンでは実行できないことを指定します。|  
  
## <a name="remarks"></a>コメント  
 0x0010 と0x0070 の間の値は、参照アセンブリのサイドバイサイドの互換性機能を記述するために使用されます。 これらの値のいずれも設定されていない場合、アセンブリはサイドバイサイドで互換性があると見なされます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
- [IMetaDataAssemblyEmit インターフェイス](imetadataassemblyemit-interface.md)
