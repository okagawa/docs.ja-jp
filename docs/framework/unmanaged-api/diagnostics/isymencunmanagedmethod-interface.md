---
description: 詳細については、「ISymENCUnmanagedMethod インターフェイス」を参照してください。
title: ISymENCUnmanagedMethod インターフェイス
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: 59dd56c20279b2507fc4432182d0abb5b3e9c289
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790322"
---
# <a name="isymencunmanagedmethod-interface"></a>ISymENCUnmanagedMethod インターフェイス

エディットコンティニュ機能に関する情報を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDocumentsForMethod メソッド](isymencunmanagedmethod-getdocumentsformethod-method.md)|このメソッドに行が含まれているドキュメントを取得します。|  
|[GetDocumentsForMethodCount メソッド](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|このメソッドに行があるドキュメントの数を取得します。|  
|[GetFileNameFromOffset メソッド](isymencunmanagedmethod-getfilenamefromoffset-method.md)|オフセットに関連付けられた行のファイル名を取得します。|  
|[GetLineFromOffset メソッド](isymencunmanagedmethod-getlinefromoffset-method.md)|オフセットに関連付けられている行情報を取得します。|  
|[GetSourceExtentInDocument メソッド](isymencunmanagedmethod-getsourceextentindocument-method.md)|特定のドキュメント内のメソッドの最小の開始行と最大の終了行を取得します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
