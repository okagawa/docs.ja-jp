---
description: 詳細については、「IMetaDataConverter インターフェイス」を参照してください。
title: IMetaDataConverter インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: 6ed84083bad924e760c576afe485bd7ccad012cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789256"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter インターフェイス

タイプ ライブラリをそれぞれのメタデータ署名にマップして、一方から他方に変換するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo メソッド](imetadataconverter-getmetadatafromtypeinfo-method.md)|指定したインスタンスによって参照されるタイプライブラリのメタデータシグネチャを表す [IMetaDataImport](imetadataimport-interface.md) インスタンスへのポインターを取得し `ITypeInfo` ます。|  
|[GetMetaDataFromTypeLib メソッド](imetadataconverter-getmetadatafromtypelib-method.md)|`IMetaDataImport`指定したインスタンスによって表されるタイプライブラリのメタデータ署名を表すインスタンスへのポインターを取得し `ITypeLib` ます。|  
|[GetTypeLibFromMetaData メソッド](imetadataconverter-gettypelibfrommetadata-method.md)|指定した `ITypeLib` モジュール名およびライブラリ名を持つタイプライブラリを表すインスタンスへのポインターを取得します。|  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](metadata-interfaces.md)
- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
