---
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
ms.openlocfilehash: 3f34be833d3ccb5c636d2c5f18ccb6e216ef2c49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709077"
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
