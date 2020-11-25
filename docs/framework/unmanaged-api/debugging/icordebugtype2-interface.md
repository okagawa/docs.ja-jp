---
title: ICorDebugType2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 0d5fffe4350cc1f58acf588f288db3bdb7e213d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725669"
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2 インターフェイス

によって、テキスト型または複合型 (ユーザー定義型) の型識別子を取得するために、を拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド||  
|------------|-|  
|[GetTypeID メソッド](icordebugtype2-gettypeid-method.md)|この型の [COR_TYPEID](cor-typeid-structure.md) を取得します。|  
  
## <a name="remarks"></a>注釈  

 このインターフェイスは、テキストの型インターフェイスの論理上の拡張機能です。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="example"></a>例  

 次のコードフラグメントは、 [ICorDebugType2:: GetTypeID](icordebugtype2-gettypeid-method.md) メソッドの使用方法を示しています。  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
