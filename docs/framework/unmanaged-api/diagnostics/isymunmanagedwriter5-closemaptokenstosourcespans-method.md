---
description: '詳細について: ISymUnmanagedWriter5:: CloseMapTokensToSourceSpans メソッド'
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 687a853441a4406c2eb0a9c4b3d5d59df3575e1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761656"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a>ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド

トークンとソースの間のマッピング情報については、特別なカスタムデータセクションを閉じます。 閉じた後は、マッピング情報を追加することはできません。  
  
## <a name="syntax"></a>構文  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>戻り値  

 `HRESULT` が返されます。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter5 インターフェイス](isymunmanagedwriter5-interface.md)
