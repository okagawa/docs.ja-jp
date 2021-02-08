---
description: 詳細については、「ICorDebugAppDomain3 インターフェイス」を参照してください。
title: ICorDebugAppDomain3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
ms.openlocfilehash: 6575aa685759102443babeaf82774e6221b80693
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772212"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 インターフェイス

アプリケーションドメインに現在読み込まれている Windows ランタイム型のマネージ表現に関する情報を取得するメソッドを提供します。 このインターフェイスは、"ICorDebugAppDomain2" というインターフェイスを拡張したものです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)|キャッシュされているすべての Windows ランタイム型の列挙子を取得します。|  
|[ICorDebugAppDomain3:: GetCachedWinRTTypesForIIDs](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|インターフェイス識別子に基づいて、アプリケーションドメイン内のキャッシュされた Windows ランタイム型の列挙子を取得します。|  
  
## <a name="remarks"></a>解説  

 このインターフェイスは、デバッガーがの関数評価呼び出しと共に使用することを意図 `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)` しています。 メソッドが Windows ランタイムサーバーオブジェクトでサポートされているインターフェイス識別子を取得すると、デバッガーはこのインターフェイスで定義されているメソッドを使用して、これらのインターフェイスに対応するマネージ型にマップすることができます。  
  
 このインターフェイスのインスタンスを取得するには、の `QueryInterface` インスタンス上でを実行します。または、ICorDebugAppDomain2 インターフェイスです。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** Windows ランタイム  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
