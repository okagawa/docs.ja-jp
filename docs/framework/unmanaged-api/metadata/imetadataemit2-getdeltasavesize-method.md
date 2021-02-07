---
description: '詳細について: IMetaDataEmit2:: GetDeltaSaveSize メソッド'
title: IMetaDataEmit2::GetDeltaSaveSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: d7b5eae7f89a5465876083c5cc8021330d3c59de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745763"
---
# <a name="imetadataemit2getdeltasavesize-method"></a>IMetaDataEmit2::GetDeltaSaveSize メソッド

現在のエディットコンティニュセッションの結果として得られるメタデータサイズの変更を示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `fSave`  
 から [CorSaveSize](corsavesize-enumeration.md) 値の1つ。必要な精度のレベルを示します。 .NET Framework バージョン2.0 では、このパラメーターは無視されます。  
  
 `pdwSaveSize`  
 入出力メタデータのサイズの変更。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
