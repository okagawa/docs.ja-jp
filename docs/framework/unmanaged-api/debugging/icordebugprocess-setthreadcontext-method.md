---
description: '詳細情報: テキスト処理:: SetThreadContext メソッド'
title: ICorDebugProcess::SetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 3576c3bf3159e3960e7d2d4601ac2fb67d7218f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753979"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext メソッド

このプロセス内の指定されたスレッドのコンテキストを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `threadID`  
 からコンテキストを設定するスレッドの ID。  
  
 `contextSize`  
 [in] `context` 配列のサイズ。  
  
 `context`  
 からスレッドのコンテキストを記述するバイト配列。  
  
 コンテキストは、スレッドが実行されているプロセッサのアーキテクチャを指定します。  
  
## <a name="remarks"></a>解説  

 デバッガーは、Win32 関数ではなく、このメソッドを呼び出す必要があります。これは、 `SetThreadContext` スレッドが実際には "ハイジャック" 状態にあり、そのコンテキストが一時的に変更されている可能性があるためです。 このメソッドは、スレッドがネイティブコード内にある場合にのみ使用してください。 マネージコード内のスレッドには、コード [を使用し](icordebugregisterset-interface.md) ます。 アウトオブバンド (OOB) デバッグイベント中は、スレッドのコンテキストを変更する必要はありません。  
  
 渡されるデータは、現在のプラットフォームのコンテキスト構造である必要があります。  
  
 不適切に使用された場合、このメソッドはランタイムを破損する可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
