---
title: ICorDebugProcess5::EnumerateGCReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: 0d98df05291ed8405addcfd183d7e02332e4e025
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209696"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences メソッド
プロセスでガベージコレクトされるすべてのオブジェクトの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `enumerateWeakReferences`  
 から弱い参照も列挙するかどうかを示すブール値。 がの場合 `enumerateWeakReferences` `true` 、 `ppEnum` 列挙子には、厳密な参照と弱い参照の両方が含まれます。 がの場合 `enumerateWeakReferences` `false` 、列挙子には厳密な参照のみが含まれます。  
  
 `ppEnum`  
 入出力ガベージコレクションの対象となるオブジェクトの列挙子[である、](icordebuggcreferenceenum-interface.md)ツールのアドレスへのポインターです。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、プロセス内の任意のマネージオブジェクトの完全なルートチェーンを確認する方法を提供し、オブジェクトがまだアクティブである理由を判断するために使用できます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
