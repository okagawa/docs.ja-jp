---
title: ISymUnmanagedWriter2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 6feb48b7c78dda64ba372e470b83ffb14f21f2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683330"
---
# <a name="isymunmanagedwriter2-interface"></a>ISymUnmanagedWriter2 インターフェイス

シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。 このインターフェイスは、 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) インターフェイスを拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DefineConstant2 メソッド](isymunmanagedwriter2-defineconstant2-method.md)|定数値の名前を定義します。|  
|[DefineGlobalVariable2 メソッド](isymunmanagedwriter2-defineglobalvariable2-method.md)|グローバル変数を 1 つ定義します。|  
|[DefineLocalVariable2 メソッド](isymunmanagedwriter2-definelocalvariable2-method.md)|現在の構文のスコープの変数を 1 つ定義します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter3 インターフェイス](isymunmanagedwriter3-interface.md)
