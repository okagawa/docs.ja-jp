---
title: ICLRAssemblyIdentityManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: 41d049c931091d2cc0b41bd1e9d74b3c15d7878d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679261"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager インターフェイス

ホストと、アセンブリに関する共通言語ランタイム (CLR) 間の通信をサポートするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBindingIdentityFromFile メソッド](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|指定したファイルパスにあるアセンブリのアセンブリ id バインドデータを取得します。|  
|[GetBindingIdentityFromStream メソッド](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|指定したストリーム内のアセンブリの正規アセンブリ id データを取得します。|  
|[GetCLRAssemblyReferenceList メソッド](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|指定された部分アセンブリ id のリストから [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) インスタンスを取得します。|  
|[GetProbingAssembliesFromReference メソッド](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|指定した id を持つアセンブリによって参照されるアセンブリ id の [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 列挙子を取得します。|  
|[GetReferencedAssembliesFromFile メソッド](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|指定したファイルパスにあるアセンブリによって参照されるアセンブリのリストを含む [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) インスタンスを取得します。|  
|[GetReferencedAssembliesFromStream メソッド](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|`ICLRReferenceAssemblyEnum`指定したストリーム内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納しているオブジェクトへのポインターを取得します。|  
|[IsStronglyNamed メソッド](iclrassemblyidentitymanager-isstronglynamed-method.md)|指定したアセンブリに厳密な名前が付けられているかどうかを示す値を取得します。|  
  
## <a name="remarks"></a>注釈  

 `ICLRAssemblyIdentityManager`のインスタンスを取得し `ICLRAssemblyReferenceList` 、アセンブリ id を列挙するには、を使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyReferenceList インターフェイス](iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum インターフェイス](iclrprobingassemblyenum-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
