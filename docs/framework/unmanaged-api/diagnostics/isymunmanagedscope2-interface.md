---
description: 詳細については、「ISymUnmanagedScope2 インターフェイス」を参照してください。
title: ISymUnmanagedScope2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: a15094da68b00dbec454b2f6a642ac333f9a34ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763151"
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2 インターフェイス

メソッド内の構文のスコープを表します。 このインターフェイスは、スコープ内で定義された定数に関する情報を取得するメソッドを使用して、 [ISymUnmanagedScope](isymunmanagedscope-interface.md) インターフェイスを拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetConstantCount メソッド](isymunmanagedscope2-getconstantcount-method.md)|このスコープ内で定義されている定数の数を取得します。|  
|[GetConstants メソッド](isymunmanagedscope2-getconstants-method.md)|このスコープ内で定義されているローカル定数を取得します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope インターフェイス](isymunmanagedscope-interface.md)
