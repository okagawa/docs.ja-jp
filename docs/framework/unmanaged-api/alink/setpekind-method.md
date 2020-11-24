---
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
ms.openlocfilehash: be8a11cbf70e2c6f19ace67648b124515c1fb3c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680041"
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
