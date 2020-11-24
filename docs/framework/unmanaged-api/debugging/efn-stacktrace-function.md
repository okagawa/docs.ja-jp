---
title: _EFN_StackTrace 関数
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
ms.openlocfilehash: 9b7624c2902d17e437cda9a0a84ddf288323b577
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676193"
---
# <a name="_efn_stacktrace-function"></a>\_EFN \_ StackTrace 関数

マネージド スタック トレースのテキスト表現および `CONTEXT` レコードの配列 (アンマネージド コードとマネージド コードの間の各移行につき 1 つ) を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `Client`  
 からデバッグ中のクライアント。  
  
 `wszTextOut`  
 入出力スタックトレースのテキスト表現。  
  
 `puiTextLength`  
 入出力内の文字数へのポインター `wszTextOut` 。  
  
 `pTransitionContexts`  
 入出力遷移コンテキストの配列。  
  
 `puiTransitionContextCount`  
 入出力配列内の遷移コンテキストの数へのポインター。  
  
 `uiSizeOfContext`  
 からコンテキスト構造のサイズ。  
  
 `Flags`  
 からを0または SOS_STACKTRACE_SHOWADDRESSES (0x01) のいずれかに設定すると、EBP レジスタと、各行の前に入力スタックポインター (ESP) が表示され `module!functionname` ます。  
  
## <a name="remarks"></a>注釈  

 この `_EFN_StackTrace` 構造体は、WinDbg プログラムインターフェイスから呼び出すことができます。 パラメーターは次のように使用されます。  
  
- `wszTextOut`が null で、 `puiTextLength` が null でない場合、関数はの文字列長を返し `puiTextLength` ます。  
  
- `wszTextOut`が null でない場合、関数はに `wszTextOut` よって示される場所までテキストを格納し `puiTextLength` ます。 バッファーに十分な空き領域がある場合は、正常に返されます。バッファーの長さが十分でない場合は E_OUTOFMEMORY を返します。  
  
- とが両方とも null の場合、関数の移行部分は無視され `pTransitionContexts` `puiTransitionContextCount` ます。 この場合、関数は呼び出し元に関数名のみのテキスト出力を提供します。  
  
- `pTransitionContexts`が null で、 `puiTransitionContextCount` が null でない場合、関数はで必要なコンテキストエントリの数を返し `puiTransitionContextCount` ます。  
  
- `pTransitionContexts`が null でない場合、関数はそれを長さの構造体の配列として扱い `puiTransitionContextCount` ます。 構造体のサイズはによって指定され、 `uiSizeOfContext` [simplecontext](stacktrace-simplecontext-structure.md) またはアーキテクチャのサイズである必要があり `CONTEXT` ます。  
  
- `wszTextOut` は、次の形式で記述されます。  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- 16進数のオフセットが0x0 の場合、オフセットは書き込まれません。  
  
- 現在コンテキスト内にあるスレッドにマネージコードがない場合、関数は SOS_E_NOMANAGEDCODE を返します。  
  
- パラメーターは、 `Flags` 各行の前に EBP と ESP を表示する場合は0または SOS_STACKTRACE_SHOWADDRESSES になり `module!functionname` ます。 既定値は0です。  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** SOS_Stacktrace  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ グローバル静的関数](debugging-global-static-functions.md)
