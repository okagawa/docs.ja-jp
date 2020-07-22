---
title: EMemoryCriticalLevel 列挙型
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 359dd84032fce920892631dda2615f63aa54fa6b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504382"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel 列挙型
特定のメモリ割り当てが要求されたが、満たされない場合のエラーの影響を示す値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eAppDomainCritical`|割り当てを要求したドメイン内のマネージコードを実行するために割り当てが不可欠であることを示します。 メモリを割り当てることができない場合、CLR はドメインが引き続き使用可能であることを保証できません。 ホストは、割り当てを満たすことができない場合に実行するアクションを決定します。 CLR は、を自動的に中止するように指示することも、 `AppDomain` [ICLRPolicyManager](iclrpolicymanager-interface.md)でメソッドを呼び出すことによって実行を継続できるようにすることもできます。|  
|`eProcessCritical`|は、プロセス内のマネージコードの実行に対して割り当てが不可欠であることを示します。 この値は、起動時とファイナライザーの実行時に使用されます。 メモリを割り当てることができない場合、CLR はプロセスで動作できません。 割り当てが失敗した場合、CLR は実質的に無効になります。 CLR への後続の呼び出しはすべて、HOST_E_CLRNOTAVAILABLE で失敗します。|  
|`eTaskCritical`|割り当てを要求したタスクを実行するために割り当てが不可欠であることを示します。 メモリを割り当てることができない場合、CLR はタスクを実行できることを保証できません。 エラーが発生した場合、CLR は <xref:System.Threading.ThreadAbortException> 物理操作システムスレッドでを発生させます。|  
  
## <a name="remarks"></a>解説  
 [IHostMemoryManager](ihostmemorymanager-interface.md)インターフェイスと[IHostMAlloc](ihostmalloc-interface.md)インターフェイスで定義されているメモリ割り当てメソッドは、この型のパラメーターを受け取ります。 障害の重大度に応じて、割り当て要求を直ちに失敗させるか、または満たされるまで待機するかをホストが決定できます。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMemoryNotificationCallback インターフェイス](iclrmemorynotificationcallback-interface.md)
- [ホスティングの列挙型](hosting-enumerations.md)
