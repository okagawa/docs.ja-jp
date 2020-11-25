---
title: SetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
ms.openlocfilehash: 4b0de5f9759491f1303edc978b1548e91214daf8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733751"
---
# <a name="setassemblyprops-method"></a>SetAssemblyProps メソッド

アセンブリレベルのプロパティを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 アセンブリの ID。  
  
 `FileToken`  
 プロパティを定義するファイルです。 がバインドされ `AssemblyID` ていない .netmodule を示していない場合は、NULL にすることができます。  
  
 `Option`  
 変更するオプションを示します。  
  
 `Value`  
 オプションの新しい値。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
