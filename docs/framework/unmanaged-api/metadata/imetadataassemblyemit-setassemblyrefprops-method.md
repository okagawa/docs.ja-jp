---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: e28659f3c6912489775dd09951610f19e4400942
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672748"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps メソッド

指定された `AssemblyRef` メタデータ構造体を変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ar`  
 から変更するメタデータ構造を指定するメタデータトークン `AssemblyRef` 。  
  
 `pbPublicKeyOrToken`  
 から参照アセンブリの発行元の公開キー。  
  
 `cbPublicKeyOrToken`  
 からのサイズ (バイト単位) `pbPublicKeyOrToken` 。  
  
 `szName`  
 からユーザーが判読できる、アセンブリのテキスト名。  
  
 `pMetaData`  
 からアセンブリのバージョン、プラットフォーム、およびロケール情報を格納している ASSEMBLYMETADATA インスタンスへのポインター。  
  
 `pbHashValue`  
 からアセンブリに関連付けられているハッシュデータへのポインター。  
  
 `cbHashValue`  
 からのサイズ (バイト単位) `pbHashValue` 。  
  
 `dwAssemblyRefFlags`  
 から参照アセンブリの属性を指定する [Assemblyrefflags](assemblyrefflags-enumeration.md) 値のビットごとの組み合わせ。  
  
## <a name="remarks"></a>注釈  

 メタデータ構造を作成するには `AssemblyRef` 、 [IMetaDataAssemblyEmit::D efineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) メソッドを使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](imetadataassemblyemit-interface.md)
