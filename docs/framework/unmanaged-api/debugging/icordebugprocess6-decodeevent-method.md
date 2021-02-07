---
description: '詳細について: ICorDebugProcess6::D ecodeEvent メソッド'
title: ICorDebugProcess6::DecodeEvent メソッド
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: 241b24335f96a250156effde34683c8f32a47e3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746218"
---
# <a name="icordebugprocess6decodeevent-method"></a>ICorDebugProcess6::DecodeEvent メソッド

特別に作成されたネイティブ例外デバッグ イベントのペイロードにカプセル化されたマネージド デバッグ イベントをデコードします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,
        [in] DWORD dwThreadId,
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pRecord`  
 [入力] マネージド デバッグ イベントに関する情報が含まれているネイティブ例外デバッグ イベントからバイト配列へのポインター。  
  
 `countBytes`  
 [入力] `pRecord` バイト配列にある要素数。  
  
 `format`  
 からアンマネージデバッグイベントの形式を指定する [Cordebugrecordformat](cordebugrecordformat-enumeration.md) 列挙体のメンバー。  
  
 `dwFlags`  
 [入力] ターゲット アーキテクチャに依存し、デバッグ イベントに関する追加情報を指定するビット フィールド。 Windows システムの場合は、 [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) 列挙体のメンバーになることができます。  
  
 `dwThreadId`  
 [入力] 例外がスローされたスレッドのオペレーティング システムの識別子。  
  
 `ppEvent`  
 入出力デコードされたマネージデバッグイベントを表す、 [コードオブジェクトの](icordebugdebugevent-interface.md) アドレスへのポインター。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess6 インターフェイス](icordebugprocess6-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
