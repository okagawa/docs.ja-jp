---
title: IMetaDataAssemblyEmit::DefineAssembly メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 6d783e27c60db7381025f3b2382728e3996323ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725730"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly メソッド

`Assembly`指定したアセンブリのメタデータを格納している構造体を作成し、関連付けられているメタデータトークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbPublicKey`  
 からアセンブリの発行元を識別する公開キー。アセンブリに厳密な名前が付けられていない場合は NULL。  
  
 `cbPublicKey`  
 からのサイズ (バイト単位) `pbPublicKey` 。  
  
 `uHashAlgId`  
 からアセンブリ内のファイルを暗号化するために使用するハッシュアルゴリズムの識別子。または、SHA-1 アルゴリズムを指定する場合は NULL。  
  
 `szName`  
 からユーザーが判読できる、アセンブリのテキスト名。 この値は、1024文字を超えないようにする必要があります。  
  
 `pMetaData`  
 からアセンブリのバージョン、プラットフォーム、およびロケール情報を格納している ASSEMBLYMETADATA インスタンスへのポインター。  
  
 `dwAssemblyFlags`  
 からアセンブリの機能を記述する [Corassemblyflags](corassemblyflags-enumeration.md) 値の組み合わせ。  
  
 `pmda`  
 入出力メタデータトークンへのポインター。  
  
## <a name="remarks"></a>注釈  

 `Assembly`マニフェスト内で定義できるメタデータ構造は1つだけです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](imetadataassemblyemit-interface.md)
