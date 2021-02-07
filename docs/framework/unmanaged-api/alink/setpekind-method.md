---
description: '詳細情報: SetPEKind メソッド'
title: SetPEKind メソッド
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: 4154e9e80b7f88b6951c9aa8da5fc23d340c96dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662300"
---
# <a name="setpekind-method"></a>SetPEKind メソッド

ポータブル実行可能ファイルの種類 (マシン固有またはコンピューターに依存しない) を決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 アセンブリの ID。  
  
 `FileToken`  
 PE の種類を設定するファイルのトークン。 がバインドされ `AssemblyID` ていない .netmodule を示していない場合は、NULL にすることができます。  
  
 `dwPEKind`  
 [Corpekind 列挙体](../metadata/corpekind-enumeration.md)によって示される PE の種類。  
  
 `dwMachine`  
 NT ヘッダーに示されている、対象コンピューターのアーキテクチャ。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [GetPEKind メソッド](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
