---
description: '詳細について: IMetaDataEmit::D efinePermissionSet メソッド'
title: IMetaDataEmit::DefinePermissionSet メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: f5c3f1466217713cb3970c805079d8f65fd429c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784081"
---
# <a name="imetadataemitdefinepermissionset-method"></a>IMetaDataEmit::DefinePermissionSet メソッド

指定したメタデータシグネチャを持つアクセス許可セットの定義を作成し、そのアクセス許可セットの定義に対するトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `tk`  
 から修飾されるオブジェクト。  
  
 `dwAction`  
 から使用する宣言セキュリティの種類を指定する [CorDeclSecurity](cordeclsecurity-enumeration.md) 値です。  
  
 `pvPermission`  
 からアクセス許可 BLOB。  
  
 `cbPermission`  
 からのサイズ (バイト単位) `pvPermission` 。  
  
 `ppm`  
 入出力返されたアクセス許可トークン。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
