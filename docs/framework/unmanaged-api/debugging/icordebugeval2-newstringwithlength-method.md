---
description: '詳細について: ICorDebugEval2:: NewStringWithLength メソッド'
title: ICorDebugEval2::NewStringWithLength メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 23864dabefcb4fc12f73c66bc2d19a6cca1aacf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693526"
---
# <a name="icordebugeval2newstringwithlength-method"></a>ICorDebugEval2::NewStringWithLength メソッド

指定したコンテンツを使用して、指定した長さの文字列を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `string`  
 から文字列値へのポインター。  
  
 `uiLength`  
 から文字列の長さ。  
  
## <a name="remarks"></a>解説  

 文字列の末尾の null 文字がマネージ文字列に含まれると想定される場合、メソッドの呼び出し元は、 `NewStringWithLength` 文字列の長さに末尾の null 文字が含まれていることを確認する必要があります。  
  
 文字列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
