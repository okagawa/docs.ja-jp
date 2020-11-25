---
title: ICLRDataTarget::SetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: c135c051637858682c22db58d562e1d50eea562b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723702"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext メソッド

ターゲットプロセス内の指定されたスレッドの現在のコンテキストを設定します。 このメソッドは、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `threadID`  
 からターゲットプロセス内のスレッドのオペレーティングシステム識別子。  
  
 `contextSize`  
 からコンテキストのサイズ。  
  
 `context`  
 からコンテキストを格納しているバッファーへのポインター。  
  
 バッファー内のデータは、 `context` Win32 構造体の形式になり `CONTEXT` ます。 コンテキストはプロセッサ固有のレジスタデータを指定するため、Win32 構造体の定義は `CONTEXT` プロセッサのアーキテクチャによって異なります。 Win32 構造体の定義については、Winnt.h ヘッダーファイルを参照してください `CONTEXT` 。  
  
## <a name="remarks"></a>注釈  

 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)
