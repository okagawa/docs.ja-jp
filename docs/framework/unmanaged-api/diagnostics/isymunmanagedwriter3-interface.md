---
description: 詳細については、「ISymUnmanagedWriter3 インターフェイス」を参照してください。
title: ISymUnmanagedWriter3 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 586220af85f193b43acf0578706d9f67e3e83386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761734"
---
# <a name="isymunmanagedwriter3-interface"></a>ISymUnmanagedWriter3 インターフェイス

シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。 このインターフェイスは、 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) インターフェイスを拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Commit メソッド](isymunmanagedwriter3-commit-method.md)|これまでに書き込まれた変更をストリームにコミットします。|  
|[OpenMethod2 メソッド](isymunmanagedwriter3-openmethod2-method.md)|メソッドを開き、イメージ内の実際のセクションオフセットを提供します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter2 インターフェイス](isymunmanagedwriter2-interface.md)
