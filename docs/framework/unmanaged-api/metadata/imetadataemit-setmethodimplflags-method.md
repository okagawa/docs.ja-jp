---
description: '詳細について: IMetaDataEmit:: SetMethodImplFlags メソッド'
title: IMetaDataEmit::SetMethodImplFlags メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: ea7f3122a21c8651014e60de3629db87eeaf6260
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657836"
---
# <a name="imetadataemitsetmethodimplflags-method"></a>IMetaDataEmit::SetMethodImplFlags メソッド

指定したトークンによって参照される、継承されたメソッドの実装のメタデータシグネチャを設定または更新します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `md`  
 から変更するメソッドのトークン。  
  
 `dwImplFlags`  
 からメソッド実装機能を指定する [Cormethodimpl](cormethodimpl-enumeration.md) 列挙値の組み合わせ。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
