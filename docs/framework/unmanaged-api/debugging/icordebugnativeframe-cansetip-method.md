---
description: '詳細については、次の情報を参照してください: テキストボックス'
title: ICorDebugNativeFrame::CanSetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: ec8f257b44143332063d7579b62dcc2afe0fccdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637860"
---
# <a name="icordebugnativeframecansetip-method"></a>ICorDebugNativeFrame::CanSetIP メソッド

命令ポインター (IP) をネイティブコード内の指定されたオフセット位置に安全に設定できるかどうかを示す HRESULT を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `nOffset`  
 から命令ポインターに必要な設定。  
  
## <a name="remarks"></a>解説  

 次のメソッドを使用して、 `CanSetIP` [テキストボックス:: SetIP](icordebugnativeframe-setip-method.md) メソッドを呼び出します。 が `CanSetIP` S_OK 以外の HRESULT を返した場合でもを呼び出すことはでき `ICorDebugNativeFrame::SetIP` ますが、デバッガーがデバッグ中のコードの安全かつ適切な実行を継続する保証はありません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
