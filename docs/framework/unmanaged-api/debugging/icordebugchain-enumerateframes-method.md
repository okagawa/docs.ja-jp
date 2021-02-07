---
description: '詳細については、次を参照してください: EnumerateFrames メソッド'
title: ICorDebugChain::EnumerateFrames メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: 45bf69760eeccebada743d81e859a19e209b611a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711597"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames メソッド

チェーン内のすべてのマネージスタックフレームが格納された列挙子を取得します。これは、最新のフレームから始まります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppFrames`  
 入出力スタックフレームの列挙子である、テキストフレームの列挙型オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 チェーンは、スレッドの物理呼び出し履歴を表します。  
  
 メソッドは、 `EnumerateFrames` マネージドチェーンに対してのみ呼び出す必要があります。 デバッグ API には、アンマネージチェーンに含まれるフレームを取得するためのメソッドが用意されていません。 デバッガーは、この情報を取得するために他の手段を使用する必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
