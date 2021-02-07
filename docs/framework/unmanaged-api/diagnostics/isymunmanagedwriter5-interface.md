---
description: 詳細については、「ISymUnmanagedWriter5 インターフェイス」を参照してください。
title: ISymUnmanagedWriter5 インターフェイス
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 0902385576e1eed17cea672b04858c7e3ef7add8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761630"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 インターフェイス

ISymUnmanagedWriter5 インターフェイス。  
  
## <a name="syntax"></a>構文  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>メソッド  

 このインターフェイスには、次のメソッドが含まれています。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans メソッド](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|トークンとソースの間のマッピング情報については、特別なカスタムデータセクションを閉じます。 閉じた後は、マッピング情報を追加することはできません。|  
|[MapTokenToSourceSpan メソッド](isymunmanagedwriter5-maptokentosourcespan-method.md)|指定されたメタデータトークンを、指定されたソースファイル内の指定されたソース行スパンにマップします。<br /><br /> [Openmaptokenstosourcespans メソッド](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)の呼び出しの間で、を呼び出す必要があります。|  
|[OpenMapTokensToSourceSpans メソッド](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|特別なカスタムデータセクションを開き、トークンからソースまでの範囲マッピング情報をに出力します。 メソッドが既に開いている場合や、その逆の場合にこのセクションを開くと、エラーになります。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 インターフェイス](isymunmanagedwriter4-interface.md)
