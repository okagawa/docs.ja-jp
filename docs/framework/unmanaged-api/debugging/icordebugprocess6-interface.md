---
description: 詳細については、「ICorDebugProcess6 インターフェイス」を参照してください。
title: ICorDebugProcess6 インターフェイス
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: f303670d0667a80507bc623f9af037759fdde463
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691459"
---
# <a name="icordebugprocess6-interface"></a>ICorDebugProcess6 インターフェイス

ICorDebugProcess インターフェイスを論理的に拡張し、ネイティブ例外デバッグ イベントにエンコードされたマネージド デバッグ イベントのデコードや仮想モジュール分割などの機能を有効にします。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DecodeEvent メソッド](icordebugprocess6-decodeevent-method.md)|特別に作成されたネイティブ例外デバッグ イベントのペイロードにカプセル化されたマネージド デバッグ イベントをデコードします。|  
|[EnableVirtualModuleSplitting メソッド](icordebugprocess6-enablevirtualmodulesplitting-method.md)|仮想モジュール分割を有効または無効にします。|  
|[GetCode メソッド](icordebugprocess6-getcode-method.md)|特定のコード アドレスで、マネージド コードに関する情報を取得します。|  
|[GetExportStepInfo メソッド](icordebugprocess6-getexportstepinfo-method.md)|マネージド コードのステップ実行に役立つランタイム エクスポート関数の情報を提供します。|  
|[MarkDebuggerAttached メソッド](icordebugprocess6-markdebuggerattached-method.md)|.NET Framework クラス ライブラリの <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドが `true` を返すように、デバッグ対象の内部状態を変更します。|  
|[ProcessStateChanged メソッド](icordebugprocess6-processstatechanged-method.md)|プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは .NET ネイティブでのみ使用可能です。 インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
