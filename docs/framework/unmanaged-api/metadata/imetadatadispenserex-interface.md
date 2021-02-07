---
description: 詳細については、「IMetaDataDispenserEx インターフェイス」を参照してください。
title: IMetaDataDispenserEx インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: d940ac20eaad4b930ab17fb2d194d3b03bd4cf3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753537"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx インターフェイス

[IMetaDataDispenser インターフェイス](imetadatadispenser-interface.md)インターフェイスを拡張して、メタデータ api が現在のメタデータスコープに対してどのように動作するかを制御する機能を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FindAssembly メソッド](imetadatadispenserex-findassembly-method.md)|このメソッドは実装されていません。 呼び出された場合は E_NOTIMPL を返します。|  
|[FindAssemblyModule メソッド](imetadatadispenserex-findassemblymodule-method.md)|このメソッドは実装されていません。 呼び出された場合は E_NOTIMPL を返します。|  
|[GetCORSystemDirectory メソッド](imetadatadispenserex-getcorsystemdirectory-method.md)|現在の共通言語ランタイム (CLR) が格納されているディレクトリを取得します。 このメソッドは、アウトプロセスデバッガーでの使用に対してのみサポートされています。 別のコンポーネントから呼び出された場合は、E_NOTIMPL を返します。|  
|[GetOption メソッド](imetadatadispenserex-getoption-method.md)|現在のメタデータスコープの指定したオプションの値を取得します。 オプションは、現在のメタデータスコープへの呼び出しの処理方法を制御します。|  
|[OpenScopeOnITypeInfo メソッド](imetadatadispenserex-openscopeonitypeinfo-method.md)|このメソッドは実装されていません。 呼び出された場合は E_NOTIMPL を返します。|  
|[SetOption メソッド](imetadatadispenserex-setoption-method.md)|指定されたオプションを、現在のメタデータスコープの指定された値に設定します。 オプションは、現在のメタデータスコープへの呼び出しの処理方法を制御します。|  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](metadata-interfaces.md)
- [IMetaDataDispenser インターフェイス](imetadatadispenser-interface.md)
- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
