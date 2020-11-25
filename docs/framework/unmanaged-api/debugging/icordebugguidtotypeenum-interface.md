---
title: ICorDebugGuidToTypeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: 149c5b09639c8809e736ade09566e7b1b530e3eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705712"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum インターフェイス

整数のセットとそれに対応する型の間のマッピングを定義する列挙子を提供します。これは、テキストインスタンスによって表されます。 このインターフェイスは、ICorDebugEnum インターフェイスからメソッドを継承します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[いいね Totypeenum:: Next](icordebugguidtotypeenum-next-method.md)|Guid を型情報にマップする、指定された数の [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) インスタンスを取得します。|  
  
## <a name="remarks"></a>注釈  

 `ICorDebugGuidToTypeEnum`インターフェイスオブジェクトは、 [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)メソッドを呼び出すことによって取得できます。 デバッガーは、このインターフェイスの[Next](icordebugguidtotypeenum-next-method.md)メソッドを呼び出して、 [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)メソッドの呼び出しに使用されるアプリケーションドメインに読み込まれた Windows ランタイム型のマネージ表現のマッピングを表す[cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md)オブジェクトを取得できます。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** Windows ランタイム  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
