---
title: ICeeGen::GetSectionBlock メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: 9ce3afded5f914ecf970d8db738becc7f5cfff84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723143"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock メソッド

コードベースのセクションブロックを取得します。  
  
 このメソッドは互換性のために残されています。使用しないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a>パラメーター  

 `section`  
 からコードベースのブロックを取得する対象となるセクション。  
  
 `len`  
 から取得するブロックの長さ。  
  
 `align`  
 からブロックの最初のバイトを揃えるために使用する、セクションの先頭を基準とするバイト。 これは、セクション内のブロックの位置です。  
  
 `ppBytes`  
 入出力取得されたブロックのアドレスを受け取る場所へのポインター。  
  
## <a name="remarks"></a>注釈  

 `GetSectionBlock`他のメソッドによって処理されない特殊なセクション要件がある場合にのみ、を呼び出します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICeeGen インターフェイス](iceegen-interface.md)
