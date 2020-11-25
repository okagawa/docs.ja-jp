---
title: ISymUnmanagedScope インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: 9256342ad3a91e6770d6fd19d9d2f94fab267d3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725886"
---
# <a name="isymunmanagedscope-interface"></a>ISymUnmanagedScope インターフェイス

メソッド内の構文のスコープを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetChildren メソッド](isymunmanagedscope-getchildren-method.md)|このスコープの子を取得します。|  
|[GetEndOffset メソッド](isymunmanagedscope-getendoffset-method.md)|このスコープの終了オフセットを取得します。|  
|[GetLocalCount メソッド](isymunmanagedscope-getlocalcount-method.md)|このスコープ内で定義されているローカル変数の数を取得します。|  
|[GetLocals メソッド](isymunmanagedscope-getlocals-method.md)|このスコープ内で定義されているローカル変数を取得します。|  
|[GetMethod メソッド](isymunmanagedscope-getmethod-method.md)|このスコープを格納しているメソッドを取得します。|  
|[GetNamespaces メソッド](isymunmanagedscope-getnamespaces-method.md)|このスコープ内で使用されている名前空間を取得します。|  
|[GetParent メソッド](isymunmanagedscope-getparent-method.md)|このスコープの親スコープを取得します。|  
|[GetStartOffSet メソッド](isymunmanagedscope-getstartoffset-method.md)|このスコープの開始オフセットを取得します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope2 インターフェイス](isymunmanagedscope2-interface.md)
