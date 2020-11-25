---
title: IMetaDataAssemblyImport インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: c556fe247754b363ece0c5dc60750068276ddcc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714758"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport インターフェイス

アセンブリ マニフェストの内容にアクセスして確認するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CloseEnum メソッド](imetadataassemblyimport-closeenum-method.md)|指定した列挙子へのハンドルを解放します。|  
|[EnumAssemblyRefs メソッド](imetadataassemblyimport-enumassemblyrefs-method.md)|`mdAssemblyRef`現在のメタデータスコープ内のアセンブリによって参照されるアセンブリのトークンを格納している列挙子へのインターフェイスポインターを取得します。|  
|[EnumExportedTypes メソッド](imetadataassemblyimport-enumexportedtypes-method.md)|`mdExportedType`現在のメタデータスコープ内のアセンブリによって参照される COM 型のトークンを格納している列挙子へのインターフェイスポインターを取得します。|  
|[EnumFiles メソッド](imetadataassemblyimport-enumfiles-method.md)|`mdFile`現在のメタデータスコープ内のアセンブリによって参照されるファイルのトークンを格納している列挙子へのインターフェイスポインターを取得します。|  
|[EnumManifestResources メソッド](imetadataassemblyimport-enummanifestresources-method.md)|`mdManifestResource`現在のメタデータスコープ内のアセンブリによって参照されているリソースのトークンを格納している列挙子へのインターフェイスポインターを取得します。|  
|[FindAssembliesByName メソッド](imetadataassemblyimport-findassembliesbyname-method.md)|`mdAssemblyRef`指定した名前のアセンブリのトークンの配列を取得します。|  
|[FindExportedTypeByName メソッド](imetadataassemblyimport-findexportedtypebyname-method.md)|指定し `mdExportedType` た名前の COM 型のトークンを取得します。|  
|[FindManifestResourceByName メソッド](imetadataassemblyimport-findmanifestresourcebyname-method.md)|指定し `mdManifestResource` た名前のリソースのトークンを取得します。|  
|[GetAssemblyFromScope メソッド](imetadataassemblyimport-getassemblyfromscope-method.md)|現在のメタデータスコープ内のアセンブリのトークンを取得します。|  
|[GetAssemblyProps メソッド](imetadataassemblyimport-getassemblyprops-method.md)|指定したアセンブリのプロパティ設定を取得します。|  
|[GetAssemblyRefProps メソッド](imetadataassemblyimport-getassemblyrefprops-method.md)|指定したトークンのプロパティ設定を取得し `mdAssemblyRef` ます。|  
|[GetExportedTypeProps メソッド](imetadataassemblyimport-getexportedtypeprops-method.md)|指定した COM 型のプロパティ設定を取得します。|  
|[GetFileProps メソッド](imetadataassemblyimport-getfileprops-method.md)|指定されたファイルのプロパティ設定を取得します。|  
|[GetManifestResourceProps メソッド](imetadataassemblyimport-getmanifestresourceprops-method.md)|指定されたマニフェストリソースのプロパティ設定を取得します。|  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](metadata-interfaces.md)
- [IMetaDataAssemblyEmit インターフェイス](imetadataassemblyemit-interface.md)
