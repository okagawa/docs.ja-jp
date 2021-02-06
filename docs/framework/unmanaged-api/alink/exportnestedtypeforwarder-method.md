---
description: 詳細については、「ExportNestedTypeForwarder メソッド」を参照してください。
title: ExportNestedTypeForwarder メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: fd791e3fea76338f191fcf924d56720d257d2e8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638107"
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder メソッド

入れ子になった型の型フォワーダーを、指定されたアセンブリの型テーブルに追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 エクスポート元のアセンブリの ID。  
  
 `FileToken`  
 型を定義するファイルのファイルトークンまたはアセンブリ ID。  
  
 `TypeToken`  
 型のトークン。  
  
 `ParentType`  
 親の種類のトークン。  
  
 `pszTypename`  
 エクスポートする完全修飾型名。  
  
 `dwFlags`  
 `ComType``tdPublic`やなどのフラグ `tdNested` 。  
  
 `pType`  
 エクスポートの種類のトークンを受け取ります。 これは、入れ子にされた型を出力する場合にのみ必要です。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
