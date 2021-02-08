---
description: '詳細情報: CloseCLREnumeration 関数'
title: CloseCLREnumeration 関数
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
ms.openlocfilehash: 7669332cc23b78afbb3bf597e7d208a5f707aae5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772771"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration 関数

[列挙 Ateclrs 関数](enumerateclrs-function.md)によって返されるハンドルの配列にある有効な共通言語ランタイム (CLR) の継続スタートアップイベントをすべて閉じ、ハンドルおよび文字列パス配列のメモリを解放します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pHandleArray`  
 から [列挙機能](enumerateclrs-function.md)から返されたイベントハンドルの配列へのポインター。  
  
 `pStringArray`  
 から [列挙型 Ateclrs 関数](enumerateclrs-function.md)から返された CLR 文字列パスの配列へのポインター。  
  
 `dwArrayLength`  
 [in] `pHandleArray` または `pStringArray` (これらは同じです) のサイズ (長さ) を含む DWORD。  
  
## <a name="return-value"></a>戻り値  

 S_OK  
 [列挙 Ateclrs 関数](enumerateclrs-function.md)によって開かれたハンドルが閉じられ、ハンドルおよび文字列配列に割り当てられたメモリが解放されます。  
  
 E_INVALIDARG  
 `pHandleArray` の長さが、`dwArrayLength` に渡された長さと一致しません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 `pHandleArray` および `pStringArray` のメモリを解放できません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** dbgshim. h  
  
 **ライブラリ:** dbgshim.dll  
  
 **.NET Framework のバージョン:** 3.5 SP1
