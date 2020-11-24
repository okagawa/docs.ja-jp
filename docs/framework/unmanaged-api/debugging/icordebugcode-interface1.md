---
title: ICorDebugCode インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 03cbc1a598ba6c0166f72ff404c239763956c996
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687607"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode インターフェイス

Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](icordebugcode-createbreakpoint-method.md)|指定したオフセット位置にブレークポイントを作成します。|  
|[GetAddress メソッド](icordebugcode-getaddress-method.md)|この `ICorDebugCode` が表すコード セグメントの RVA (Relative Virtual Address) を取得します。|  
|[GetCode メソッド](icordebugcode-getcode-method.md)|指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。 このメソッドは非推奨とされました。代わりに [ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md) を使用してください。|  
|[GetEnCRemapSequencePoints メソッド](icordebugcode-getencremapsequencepoints-method.md)|実装されていません。|  
|[GetFunction メソッド](icordebugcode-getfunction-method.md)|このに関連付けられている "の関数" を取得し `ICorDebugCode` ます。|  
|[GetILToNativeMapping メソッド](icordebugcode-getiltonativemapping-method.md)|MSIL オフセットからネイティブオフセットへのマッピングを表す "COR_DEBUG_IL_TO_NATIVE_MAP" インスタンスの配列を取得します。|  
|[GetSize メソッド](icordebugcode-getsize-method.md)|この `ICorDebugCode` で表されるバイナリ コードのサイズ (バイト単位) を取得します。|  
|[GetVersionNumber メソッド](icordebugcode-getversionnumber-method.md)|この `ICorDebugCode` が表すコードのバージョンを識別する、1 から始まる数字を取得します。|  
|[IsIL メソッド](icordebugcode-isil-method.md)|この `ICorDebugCode` が MSIL でコンパイルされているかどうかを示す値を取得します。|  
  
## <a name="remarks"></a>注釈  

 `ICorDebugCode` は、MSIL またはネイティブ コードを表すことができます。 MSIL コードを表す "の関数" オブジェクトは、0個または1個 `ICorDebugCode` のオブジェクトを関連付けることができます。 ネイティブコードを表す "表示関数" オブジェクトには、任意の数のオブジェクトを関連付けることができ `ICorDebugCode` ます。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugCode3 インターフェイス](icordebugcode3-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
