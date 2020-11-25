---
title: ISymUnmanagedWriter4 インターフェイス
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: c2b57897e4f0e8b23337302f344065d79677e0c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725808"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 インターフェイス

ISymUnmanagedWriter4 インターフェイス。  
  
## <a name="syntax"></a>Syntax  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>メソッド  

 このインターフェイスには、次のメソッドが含まれています。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDebugInfoWithPadding メソッド](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|関数は [GetDebugInfo メソッド](isymunmanagedwriter-getdebuginfo-method.md) と同じですが、文字列データを固定サイズにするために、終端の null 文字の後にパス文字列がゼロで埋め込まれる点が異なり `MAX_PATH` ます。 埋め込みは、パス文字列の長さがより小さい場合にのみ指定 `MAX_PATH` します。<br /><br /> これにより、PE ファイルを区別するツールを簡単に記述できるようになります。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 インターフェイス](isymunmanagedwriter3-interface.md)
