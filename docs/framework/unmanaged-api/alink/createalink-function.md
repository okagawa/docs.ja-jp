---
title: CreateALink 関数
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: 98c6ed4657dc69554a9fcca27145f65c621492f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683732"
---
# <a name="createalink-function"></a>CreateALink 関数

アセンブリリンカーのインスタンスを作成し、指定したインターフェイスへのポインターを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`riid`|アセンブリリンカーインターフェイスの1つの物理名。|  
|`ppInterface`|正常に完了した場所には、インターフェイスへのポインターが含まれてい `riid` ます。|  
  
## <a name="requirements"></a>要件  

 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>関連項目

- [Al.exe (アセンブリ リンカー)](../../tools/al-exe-assembly-linker.md)
