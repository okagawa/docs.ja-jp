---
description: '詳細については、次のページを参照してください: EnumerateLocalVariables メソッド'
title: ICorDebugILFrame::EnumerateLocalVariables メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: 275cf7fcad32c452e6e7ebdd0774d64708a2398c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791388"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables メソッド

このフレーム内のローカル変数の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppValueEnum`  
 [出力] このフレームのローカル変数の列挙子である ICorDebugValueEnum オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 `EnumerateLocalVariables` このテキストボックスオブジェクトで表される呼び出しフレームで使用可能なローカル変数を一覧表示できる列挙子を取得します。 この一覧には、一部のローカル変数がアクティブでない可能性があるため、実行中の関数のすべてのローカル変数を含めることはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
