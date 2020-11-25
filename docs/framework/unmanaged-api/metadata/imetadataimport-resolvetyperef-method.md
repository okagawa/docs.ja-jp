---
title: IMetaDataImport::ResolveTypeRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 76c5519a6cd1b8994e2f869281f13d8269e89fde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702824"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef メソッド

<xref:System.Type>指定した TypeRef トークンによって表される参照を解決します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `tr`  
 から参照される型情報を返す TypeRef メタデータトークン。  
  
 `riid`  
 から返されるインターフェイスの IID `ppIScope` 。 通常、これは IID_IMetaDataImport になります。  
  
 `ppIScope`  
 入出力参照される型が定義されているモジュールスコープへのインターフェイス。  
  
 `ptd`  
 入出力参照された型を表す TypeDef トークンへのポインター。  
  
## <a name="remarks"></a>注釈  
  
> [!IMPORTANT]
> 複数のアプリケーションドメインが読み込まれる場合は、この方法を使用しないでください。 メソッドは、アプリケーションドメインの境界を尊重しません。 アセンブリの複数のバージョンが読み込まれ、同じ名前空間を持つ同じ型が含まれている場合、メソッドは最初に見つかった型のモジュールスコープを返します。  
  
 メソッドは、 `ResolveTypeRef` 他のモジュールで型定義を検索します。 型定義が見つかった場合は、 `ResolveTypeRef` そのモジュールスコープへのインターフェイスと、その型の TypeDef トークンを返します。  
  
 解決する型参照の解決スコープが AssemblyRef である場合、メソッドは、 `ResolveTypeRef` [IMetaDataDispenser:: openscope](imetadatadispenser-openscope-method.md) メソッドまたは [IMetaDataDispenser:: openscopeonmemory](imetadatadispenser-openscopeonmemory-method.md) メソッドの呼び出しで既に開かれているメタデータスコープ内でのみ一致を検索します。 これは、が、 `ResolveTypeRef` ディスク上またはグローバルアセンブリキャッシュ内の、アセンブリが格納されている AssemblyRef スコープからしか判断できないためです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
