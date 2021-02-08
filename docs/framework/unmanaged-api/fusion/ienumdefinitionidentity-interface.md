---
description: 詳細については、「IEnumDefinitionIdentity インターフェイス」を参照してください。
title: IEnumDefinitionIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
ms.openlocfilehash: 1055031c064115410334bbe4b20b48deee7ec4c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800163"
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity インターフェイス

オブジェクトのコレクションの列挙子として機能し `IDefinitionIdentity` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|このと同じメンバーを含む新しいオブジェクトへのインターフェイスポインターを取得し `IEnumDefinitionIdentity` `IEnumDefinitionIdentity` ます。|  
|`IEnumDefinitionIdentity::Next`|現在の位置から開始して、指定した数の `IDefinitionIdentity` オブジェクトを取得します。|  
|`IEnumDefinitionIdentity::Reset`|命令ポインターをこのの先頭に移動し `IEnumDefinitionIdentity` ます。|  
|`IEnumDefinitionIdentity::Skip`|現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IDefinitionIdentity インターフェイス](idefinitionidentity-interface.md)
