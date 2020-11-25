---
title: IMetaDataDispenser::DefineScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 87a39350986cb7bb62f76b0d9a6a9aae8f82e2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726094"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope メソッド

新しいメタデータを作成できる新しい領域をメモリ内に作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `rclsid`  
 から作成されるメタデータ構造のバージョンの CLSID。 この値は、.NET Framework バージョン2.0 の CLSID_CorMetaDataRuntime である必要があります。  
  
 `dwCreateFlags`  
 からオプションを指定するフラグ。 .NET Framework 2.0 の場合、この値は0である必要があります。  
  
 `riid`  
 から返される、必要なメタデータインターフェイスの IID。呼び出し元は、インターフェイスを使用して新しいメタデータを作成します。  
  
 の値には `riid` 、"emit" インターフェイスのいずれかを指定する必要があります。 有効な値は、IID_IMetaDataEmit、IID_IMetaDataAssemblyEmit、または IID_IMetaDataEmit2 です。  
  
 `ppIUnk`  
 入出力返されたインターフェイスへのポインター。  
  
## <a name="remarks"></a>注釈  

 `DefineScope` メモリ内メタデータテーブルのセットを作成し、メタデータの一意の GUID (モジュールバージョン識別子または MVID) を生成し、出力されるコンパイル単位のエントリをモジュールテーブルに作成します。  
  
 必要に応じて、 [IMetaDataEmit:: SetModuleProps](imetadataemit-setmoduleprops-method.md) または [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md) メソッドを使用して、メタデータスコープ全体に属性をアタッチできます。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenser インターフェイス](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx インターフェイス](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit インターフェイス](imetadataassemblyemit-interface.md)
- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
