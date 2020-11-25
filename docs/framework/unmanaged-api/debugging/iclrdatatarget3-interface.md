---
title: ICLRDataTarget3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: 7297bfa5297878dde6867a99029ac88754a05290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723585"
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 インターフェイス

例外情報へのアクセスを提供する [ICLRDataTarget2](iclrdatatarget2-interface.md) のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetExceptionRecord メソッド](iclrdatatarget3-getexceptionrecord-method.md)|ターゲット プロセスに関連付けられた例外レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。|  
|[GetExceptionContextRecord メソッド](iclrdatatarget3-getexceptioncontextrecord-method.md)|ターゲット プロセスに関連付けられているコンテキスト レコードを取得するために、CLR データ アクセス サービスによって呼び出されます。|  
|[GetExceptionThreadID メソッド](iclrdatatarget3-getexceptionthreadid-method.md)|例外をスローしたスレッドの ID を取得するために、CLR データ アクセス サービスによって呼び出されます。|  
  
## <a name="remarks"></a>注釈  

 API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。 たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。 ターゲットは、メモリ領域の変更をサポートしない可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)
- [ICLRDataTarget2 インターフェイス](iclrdatatarget2-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
