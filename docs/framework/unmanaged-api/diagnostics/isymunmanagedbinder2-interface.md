---
title: ISymUnmanagedBinder2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: c5a43f6c277f582f9f14cefe5bfba6f5300c09d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727355"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 インターフェイス

アンマネージコードのシンボルバインダーを表し、 [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) インターフェイスを拡張します。  
  
> [!IMPORTANT]
> 信頼されていないソースからプログラムデータベース (PDB) ファイルを開くと、セキュリティ上の危険があります。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReaderForFile2 メソッド](isymunmanagedbinder2-getreaderforfile2-method.md)|メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスが返されます。 [ISymUnmanagedBinder:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)メソッドよりも広範な検索を提供します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder インターフェイス](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder3 インターフェイス](isymunmanagedbinder3-interface.md)
