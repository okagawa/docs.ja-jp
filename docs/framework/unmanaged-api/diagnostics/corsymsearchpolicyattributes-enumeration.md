---
description: 詳細については、「CorSymSearchPolicyAttributes 列挙型」を参照してください。
title: CorSymSearchPolicyAttributes 列挙体
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: a9af0e96809ec8eba5c03c2e372e818c74914baf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800475"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes 列挙体

シンボルリーダーの検索を実行するときに使用するポリシーを指定します。 これらの定数は、 [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) メソッドと [ISymUnmanagedBinder3:: GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) メソッドによって使用されます。  
  
> [!IMPORTANT]
> 信頼されていないソースからプログラムデータベース (PDB) ファイルを開くと、セキュリティ上の危険があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`AllowRegistryAccess`|シンボル検索パスのレジストリを照会します。|  
|`AllowSymbolServerAccess`|シンボルサーバーにアクセスします。|  
|`AllowOriginalPathAccess`|デバッグディレクトリに指定されているパスを検索します。|  
|`AllowReferencePathAccess`|.Exe ファイルがある場所で PDB を検索します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断列挙型](diagnostics-symbol-store-enumerations.md)
