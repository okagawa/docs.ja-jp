---
description: '詳細情報: テキストボックスのインターフェイス'
title: ICorDebugNativeFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: e417184c9f1ca5136e1b4dba07820fd8242ae932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729134"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame インターフェイス

ネイティブフレームに使用される、特殊な実装のテキストフレーム。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanSetIP メソッド](icordebugnativeframe-cansetip-method.md)|命令ポインターをネイティブコード内の指定したオフセット位置に安全に設定できるかどうかを示す値を取得します。|  
|[GetIP メソッド](icordebugnativeframe-getip-method.md)|ネイティブコードへのスタックフレームのオフセットを取得します。|  
|[GetLocalDoubleRegisterValue メソッド](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|ネイティブフレームの2つのメモリレジスタに格納されている引数またはローカル変数の値を表す ICorDebugValue へのポインターを取得します。|  
|[GetLocalMemoryRegisterValue メソッド](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|指定した `ICorDebugValue` レジスタに下位ビットが格納されているローカル変数の値を表すへのポインターを取得します。上位ビットは、指定したメモリアドレスに格納されます。|  
|[GetLocalMemoryValue メソッド](icordebugnativeframe-getlocalmemoryvalue-method.md)|`ICorDebugValue`指定したメモリアドレスに格納されているローカル変数の値を表すへのポインターを取得します。|  
|[GetLocalRegisterMemoryValue メソッド](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|指定した `ICorDebugValue` レジスタに上位ビットが格納され、下位ビットが指定したメモリアドレスに格納されているローカル変数の値を表すへのポインターを取得します。|  
|[GetLocalRegisterValue メソッド](icordebugnativeframe-getlocalregistervalue-method.md)|`ICorDebugValue`引数の値または指定したネイティブレジスタに格納されているローカル変数を表すへのポインターを取得します。|  
|[GetRegisterSet メソッド](icordebugnativeframe-getregisterset-method.md)|こののレジスタセットを表す、ツール [のセットへ](icordebugregisterset-interface.md) のポインターを取得し `ICorDebugNativeFrame` ます。|  
|[SetIP メソッド](icordebugnativeframe-setip-method.md)|命令ポインターをネイティブコード内の指定されたオフセット位置に設定します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
