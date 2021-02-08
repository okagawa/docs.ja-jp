---
description: '詳細情報: IInstallReferenceItem:: GetReference メソッド'
title: IInstallReferenceItem::GetReference メソッド
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
ms.openlocfilehash: 88f5ca21b6f3494031e1cd232f71253e39d9e648
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800115"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference メソッド

この[Iinstallreferenceitem](iinstallreferenceitem-interface.md)オブジェクトによって表される[FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md)構造体へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppRefData`  
 入出力返された `FUSION_INSTALL_REFERENCE` ポインター。  
  
 `dwFlags`  
 [入力] 将来の機能拡張に備えて予約されています。 `dwFlags` 0 (ゼロ) にする必要があります。  
  
 `pvReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pvReserved` null 参照である必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IInstallReferenceItem インターフェイス](iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE 構造体](fusion-install-reference-structure.md)
