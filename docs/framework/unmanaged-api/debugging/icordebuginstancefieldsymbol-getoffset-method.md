---
description: '詳細については、次の情報を参照してください: GetOffset メソッド'
title: ICorDebugInstanceFieldSymbol::GetOffset メソッド
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 4a877b2f78adfac5c54694ab306fd7db60f266f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791167"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a>ICorDebugInstanceFieldSymbol::GetOffset メソッド

このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pcbOffset`  
 このインスタンス フィールドの親クラスにおける、このフィールドのオフセットのバイト数へのポインター。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugInstanceFieldSymbol インターフェイス](icordebuginstancefieldsymbol-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
