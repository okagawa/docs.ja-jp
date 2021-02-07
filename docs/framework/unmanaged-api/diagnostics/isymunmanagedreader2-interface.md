---
description: 詳細については、「ISymUnmanagedReader2 インターフェイス」を参照してください。
title: ISymUnmanagedReader2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: 2e6d994a3252b7fb09b2915266e3142255878a88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763619"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 インターフェイス

シンボル ストア内のドキュメント、メソッド、および変数へのアクセスを提供するシンボル リーダーを表します。 このインターフェイスは、 [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスを拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap メソッド](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|メソッドトークンとエディットコンティニュバージョン番号を指定して、シンボルリーダーメソッドを取得します。|  
|[GetMethodsInDocument メソッド](isymunmanagedreader2-getmethodsindocument-method.md)|指定されたドキュメントに行情報が含まれるすべてのメソッドを取得します。|  
|[GetSymAttributePreRemap メソッド](isymunmanagedreader2-getsymattributepreremap-method.md)|名前に基づいてカスタム属性を取得します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader インターフェイス](isymunmanagedreader-interface.md)
