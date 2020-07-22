---
title: EClrOperation 列挙型
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: e7cb1c2070e760258e548d2f45e3b6ed11e046c4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616321"
---
# <a name="eclroperation-enumeration"></a>EClrOperation 列挙型
ホストがポリシーアクションを適用できる操作のセットについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|ホストは、 <xref:System.AppDomain> が正常でない状態でアンロードされた場合に実行されるポリシーアクションを指定できます。|  
|`OPR_AppDomainUnload`|ホストは、がアンロードされたときに実行されるポリシーアクションを指定でき <xref:System.AppDomain> ます。|  
|`OPR_FinalizerRun`|ホストは、ファイナライザーの実行時に実行されるポリシーアクションを指定できます。|  
|`OPR_ProcessExit`|ホストは、プロセスが終了したときに実行するポリシーアクションを指定できます。|  
|`OPR_ThreadAbort`|ホストは、スレッドが中止されたときに実行されるポリシーアクションを指定できます。|  
|`OPR_ThreadRudeAbortInCriticalRegion`|ホストは、コードの重要な領域でルースレッドの中止が発生したときに実行されるポリシーアクションを指定できます。|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|ホストは、非クリティカルなコード領域で、ルードスレッドの中止が発生したときに実行するポリシーアクションを指定できます。|  
  
## <a name="remarks"></a>解説  
 共通言語ランタイム (CLR) の信頼性インフラストラクチャでは、コードの重要な領域で発生する中止とリソース割り当ての失敗と、コードの重要ではない領域で発生するエラーを区別します。 この区別は、コード内でエラーが発生した場所に応じて、ホストがさまざまなポリシーを設定できるように設計されています。  
  
 *コードの重要な領域*は、タスクの中止、またはリソースの要求を完了できないことが CLR によって保証されない場合、現在のタスクにのみ影響します。 たとえば、タスクがロックを保持していて、メモリ割り当て要求の発生時に失敗したことを示す HRESULT を受け取った場合、には、 <xref:System.AppDomain> <xref:System.AppDomain> 同じロックを待機している他のタスクが含まれている可能性があるため、そのタスクを中止しての安定性を保証するだけでは不十分です。 現在のタスクを破棄すると、その他のタスクが応答を停止する可能性があります。 このような場合、ホストは、潜在的に不安定になるリスクではなく、全体をアンロードする機能を必要とし <xref:System.AppDomain> ます。  
  
 一方、クリティカルでは*ないコード領域*とは、CLR が、エラーが発生したタスクのみに影響を与えることを CLR が保証できる領域です。  
  
 また、この CLR では、グレースフルとグレースフルの (ルード) 中止が区別されます。 一般に、通常または正常な中止では、タスクを中止する前に例外処理ルーチンとファイナライザーを実行するすべての作業を行います。ただし、ルードアボートではこのような保証は行われません。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EClrFailure 列挙型](eclrfailure-enumeration.md)
- [EPolicyAction 列挙型](epolicyaction-enumeration.md)
- [ICLRPolicyManager インターフェイス](iclrpolicymanager-interface.md)
- [IHostPolicyManager インターフェイス](ihostpolicymanager-interface.md)
- [ホスティングの列挙体](hosting-enumerations.md)
