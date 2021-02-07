---
description: '詳細については、次を参照してください: IMetaDataTables 許容:: GetGuid メソッド'
title: IMetaDataTables::GetGuid メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 9c3b8b11bb2f6a1abc3c55d953e1cbfbd7ee8622
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688170"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid メソッド

指定したインデックス位置にある行から GUID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ixGuid`  
 からGUID の取得元となる行のインデックス。  
  
 `ppGuid`  
 入出力GUID へのポインターへのポインター。  
  
## <a name="remarks"></a>解説  

  このメソッドは、一貫性のある結果を返さないため、使用しないことをお勧めします。 GUID テーブルの詳細については、共通言語基盤 (CLI) のドキュメント (特に「パーティション II: メタデータの定義とセマンティクス」) を参照してください。 ドキュメントはオンラインで入手できます。「 [Ecma C# および共通言語基盤の標準](../../../standard/components.md#applicable-standards) と [標準 ecma-335-共通言語基盤 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)」を参照してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](imetadatatables2-interface.md)
